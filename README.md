# currency-converter-application
import requests

def get_exchange_rate(api_key, base_currency, target_currency):
    url = f"https://v6.exchangerate-api.com/v6/{api_key}/pair/{base_currency}/{target_currency}"
    response = requests.get(url)
    data = response.json()
    
    if data['result'] == 'success':
        return data['conversion_rate']
    else:
        raise Exception(f"API error: {data.get('error-type', 'Unknown error')}")

def convert_currency(api_key, amount, base_currency, target_currency):
    rate = get_exchange_rate(api_key, base_currency.upper(), target_currency.up_
