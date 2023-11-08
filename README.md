# infotrixs
import requests # imports the requests library which is used for making HTTP requests to API
print("Welcome to weather checking")
def display_weather(city_name):
    api_key = "3027ee0d52bcbee506dfdb8d4bbaf44b"
    if not city_name.isalpha():#checks if the city_name provided by the user contains only alphabetic characters
        print("Invalid city name. Please enter a valid city name with alphabetic characters.")
        return
    url = f'http://api.openweathermap.org/data/2.5/weather?q={city_name}&appid={api_key}'
    response = requests.get(url) #sends HTTP GET request to the URL provided

    if response.status_code == 200:
        kelvin = 273 #used for converting temperature from Kelvin to Celsius
        weather_info = response.json()# parses the JSON response from API into Python dictionary storing it in weather_info variable
        temp = int(weather_info['main']['temp'] - kelvin)#converting temperature to celsius
        weather = f"Weather for {city_name}\nTemperature (Celsius): {temp}°"
    else:
        weather = f"Weather for '{city_name}' not found!\nKindly enter a valid city name."

    print(weather)
while True:
    if __name__ == "__main__":# conditional block to check the script is being run directly as the main program
        city_name = input("Enter a city name:")
        display_weather(city_name)#calling function & city_name as argument

