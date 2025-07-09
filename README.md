# collage-proj
dont pay attetion

#include <DHT.h>

#define DHTPIN 4     // GPIO4 (D4) - куда подключён DATA
#define DHTTYPE DHT11

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(115200);
  dht.begin();
}

void loop() {
  delay(2000);  // Ждём 2 секунды между измерениями
  
  float humidity = dht.readHumidity();     // Влажность (%)
  float temperature = dht.readTemperature();  // Температура (°C)
  
  // Проверяем, удалось ли считать данные
  if (isnan(humidity) || isnan(temperature)) {
    Serial.println("Ошибка чтения датчика!");
    return;
  }
  
  Serial.print("Температура: ");
  Serial.print(temperature);
  Serial.print(" °C\t");
  Serial.print("Влажность: ");
  Serial.print(humidity);
  Serial.println(" %");
}
