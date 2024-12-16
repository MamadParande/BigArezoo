# BigArezoo
// تولدت مبارک ایرانی
#include "pitches.h"

#define BUZZER_PIN 9

int melody[] = {
  NOTE_G4, NOTE_G4, NOTE_A4, NOTE_G4, NOTE_C5, NOTE_B4, // تولدت مبارک
  NOTE_G4, NOTE_G4, NOTE_A4, NOTE_G4, NOTE_D5, NOTE_C5, // تولدت مبارک
  NOTE_G4, NOTE_G4, NOTE_G5, NOTE_E5, NOTE_C5, NOTE_B4, NOTE_A4, // بیا شمع‌ها رو فوت کن
  NOTE_F5, NOTE_F5, NOTE_E5, NOTE_C5, NOTE_D5, NOTE_C5 // که صد سال زنده باشی
};

int durations[] = {
  4, 4, 4, 4, 4, 2, // تولدت مبارک
  4, 4, 4, 4, 4, 2, // تولدت مبارک
  4, 4, 4, 4, 4, 4, 2, // بیا شمع‌ها رو فوت کن
  4, 4, 4, 4, 4, 2 // که صد سال زنده باشی
};

void setup() {
  pinMode(BUZZER_PIN, OUTPUT);
}

void loop() {
  int size = sizeof(durations) / sizeof(int);

  for (int note = 0; note < size; note++) {
    int duration = 1000 / durations[note];
    tone(BUZZER_PIN, melody[note], duration);

    int pauseBetweenNotes = duration * 1.30;
    delay(pauseBetweenNotes);

    noTone(BUZZER_PIN);
  }

  delay(2000); // مکث قبل از تکرار آهنگ
}
