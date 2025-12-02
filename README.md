# sprint1/dht22_web.py - Simple DHT22 reader + web server
from flask import Flask
import Adafruit_DHT
import time

app = Flask(__name__)
sensor = Adafruit_DHT.DHT22
pin = 4

@app.route("/")
def home():
    h, t = Adafruit_DHT.read_retry(sensor, pin)
    if h is not None and t is not None:
        return f"<h1>Smart Home - Sprint 1</h1><p>Temperature: {t:.1f}°C</p><p>Humidity: {h:.1f}%</p>"
    else:
        return "<h1>Sensor error</h1>"

if __name__ == "__main__":
    app.run(host='0.0.0.0', port=5000)
    ## Sprint 1 – Completed
- DHT22 sensor successfully reads temperature and humidity
- Simple Flask web server running on port 5000
- Demo: http://[Raspberry-Pi-IP]:5000
