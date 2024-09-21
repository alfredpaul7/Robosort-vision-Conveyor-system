#include <Servo.h>
#include "esp_camera.h"
#include <edgeimpulse_inferencing.h> // Modify with your project title
#include "edge-impulse-sdk/dsp/image/image.hpp"
#include <Wire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>

// Define the GPIO pins for the six servos
#define SERVO_PIN1 2
#define SERVO_PIN2 4
#define SERVO_PIN3 12
#define SERVO_PIN4 13
#define SERVO_PIN5 14
#define SERVO_PIN6 15

// Define the GPIO pin for the IR sensor
#define IR_SENSOR_PIN 1 // Adjust as needed

// Camera pin definitions for ESP32-CAM
#define PWDN_GPIO_NUM     -1
#define RESET_GPIO_NUM    -1
#define XCLK_GPIO_NUM      4
#define SIOD_GPIO_NUM     18
#define SIOC_GPIO_NUM     23

#define Y9_GPIO_NUM       36
#define Y8_GPIO_NUM       37
#define Y7_GPIO_NUM       38
#define Y6_GPIO_NUM       39
#define Y5_GPIO_NUM       35
#define Y4_GPIO_NUM       34
#define Y3_GPIO_NUM       5
#define Y2_GPIO_NUM       17
#define VSYNC_GPIO_NUM    25
#define HREF_GPIO_NUM     26
#define PCLK_GPIO_NUM     27

// Display defines
#define SCREEN_WIDTH 128
#define SCREEN_HEIGHT 64
#define OLED_RESET -1
#define SCREEN_ADDRESS 0x3C
Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, OLED_RESET);

// Servo objects for each servo motor
Servo servoMotor1;
Servo servoMotor2;
Servo servoMotor3;
Servo servoMotor4;
Servo servoMotor5;
Servo servoMotor6;

// Variables for object and color detection
bool blackColorDetected = false;
bool yellowColorDetected = false;
bool whiteColorDetected = false;
bool objectDetected = false;

// Initialize the camera
void initCamera() {
    camera_config_t config;
    config.ledc_channel = LEDC_CHANNEL_0;
    config.ledc_timer = LEDC_TIMER_0;
    config.pin_d0 = Y2_GPIO_NUM;
    config.pin_d1 = Y3_GPIO_NUM;
    config.pin_d2 = Y4_GPIO_NUM;
    config.pin_d3 = Y5_GPIO_NUM;
    config.pin_d4 = Y6_GPIO_NUM;
    config.pin_d5 = Y7_GPIO_NUM;
    config.pin_d6 = Y8_GPIO_NUM;
    config.pin_d7 = Y9_GPIO_NUM;
    config.pin_xclk = XCLK_GPIO_NUM;
    config.pin_pclk = PCLK_GPIO_NUM;
    config.pin_vsync = VSYNC_GPIO_NUM;
    config.pin_href = HREF_GPIO_NUM;
    config.pin_sscb_sda = SIOD_GPIO_NUM;
    config.pin_sscb_scl = SIOC_GPIO_NUM;
    config.pin_pwdn = PWDN_GPIO_NUM;
    config.pin_reset = RESET_GPIO_NUM;
    config.xclk_freq_hz = 20000000;
    config.pixel_format = PIXFORMAT_JPEG;

    if (psramFound()) {
        config.frame_size = FRAMESIZE_UXGA;
        config.jpeg_quality = 10;
        config.fb_count = 2;
    } else {
        config.frame_size = FRAMESIZE_SVGA;
        config.jpeg_quality = 12;
        config.fb_count = 1;
    }

    esp_err_t err = esp_camera_init(&config);
    if (err != ESP_OK) {
        Serial.printf("Camera init failed with error 0x%x", err);
        return;
    }
}

// Function to capture and process camera input for color detection
void detectObjectsAndColors() {
    // Call Edge Impulse model to classify object and set detected color flags
    ei::signal_t signal;
    signal.total_length = EI_CLASSIFIER_INPUT_WIDTH * EI_CLASSIFIER_INPUT_HEIGHT;
    signal.get_data = &ei_camera_get_data;

    ei_impulse_result_t result = {0};
    EI_IMPULSE_ERROR err = run_classifier(&signal, &result, false);

    if (err != EI_IMPULSE_OK) {
        Serial.println("ERR: Failed to run classifier");
        return;
    }

    for (size_t ix = 0; ix < EI_CLASSIFIER_LABEL_COUNT; ix++) {
        if (strcmp(result.classification[ix].label, "black") == 0 && result.classification[ix].value > 0.5) {
            blackColorDetected = true;
        } else if (strcmp(result.classification[ix].label, "yellow") == 0 && result.classification[ix].value > 0.5) {
            yellowColorDetected = true;
        } else if (strcmp(result.classification[ix].label, "white") == 0 && result.classification[ix].value > 0.5) {
            whiteColorDetected = true;
        }
    }
    objectDetected = blackColorDetected || yellowColorDetected || whiteColorDetected;
}

void setup() {
    // Initialize Serial for debugging
    Serial.begin(115200);

    // Initialize the camera
    initCamera();

    // Attach servos to their corresponding pins
    servoMotor1.attach(SERVO_PIN1);
    servoMotor2.attach(SERVO_PIN2);
    servoMotor3.attach(SERVO_PIN3);
    servoMotor4.attach(SERVO_PIN4);
    servoMotor5.attach(SERVO_PIN5);
    servoMotor6.attach(SERVO_PIN6);

    // Initialize the IR sensor pin
    pinMode(IR_SENSOR_PIN, INPUT);

    // Initialize the display
    if (!display.begin(SSD1306_SWITCHCAPVCC, SCREEN_ADDRESS)) {
        Serial.println("SSD1306 OLED failed to initialize");
        while (true);
    }
    display.clearDisplay();
}

void loop() {
    // Read the value from the IR sensor
    int irValue = digitalRead(IR_SENSOR_PIN);

    // Control servo motor 6 based on the IR sensor value
    if (irValue == HIGH) {
        servoMotor6.write(90); // Rotate servo motor 6 to 90 degrees
    } else {
        servoMotor6.write(180); // Rotate servo motor 6 to 180 degrees
    }

    // Detect objects and colors using the camera
    detectObjectsAndColors();

    // Control servos based on detected color or object
    if (blackColorDetected) {
        // Logic for black color detected
        servoMotor1.write(120);
        servoMotor2.write(78);
        servoMotor3.write(36);
        servoMotor4.write(15);
        servoMotor5.write(85);
    } else if (yellowColorDetected) {
        // Logic for yellow color detected
        servoMotor1.write(45);
        servoMotor2.write(15);
        servoMotor3.write(85);
        servoMotor4.write(65);
        servoMotor5.write(74);
    } else if (whiteColorDetected) {
        // Logic for white color detected
        servoMotor1.write(12);
        servoMotor2.write(45);
        servoMotor3.write(78);
        servoMotor4.write(65);
        servoMotor5.write(48);
    } else if (objectDetected) {
        // Logic for any detected object
        servoMotor1.write(145);
        servoMotor2.write(12);
        servoMotor3.write(45);
        servoMotor4.write(45);
        servoMotor5.write(12);
    }

    delay(15);  // Adjust this value as needed for servo movement
}
