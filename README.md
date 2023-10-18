# PruebaSofttek
Prueba técnica de QA DEV
 1.1 Ejercicio 1: Prueba exploratoria y reporte de bugs
					
La primera tarea es encontrar un bug, nos da igual en que web de internet lo encuentres, lo importante es poder encontrarlo y reportarlo. No te preocupes porque internet está lleno de ellos.			
Haz el reporte al nivel de detalle que consideres necesario para que el equipo de desarrollo pueda encontrarlo, debuggearlo y solucionarlo. Proporciona evidencias del fallo y resultado esperado. Clasifícalo en cuanto a prioridad, impacto y probabilidad de ocurrencia.

Respuesta Ejercicio 1
Reporte de Bug:
1. Titulo y ID: 'Orden de Menor a Mayor en sitio mercadolibre.com.ar no funciona o muestra duplicados' Ticket Nro XXXX (creado en JIRA o similar)
   
2. Entorno/Ambiente donde fue encontrado: Produccion (tambien podria ser QA o PreProd, depende de donde se este probando. NOTA: al ser PROD, el bug se llama 'incidente' en vez de bug, ya que toma una seriedad/relevancia/impacto distinta/o)
   
3. Pasos para reproducir el bug:
   
   a. ingresar en www.mercadolibre.com.ar
   
   b. hacer clic en boton 'hasta 35% off'
   
   c. marcar los siguientes radiobotones: - Llegan hoy, - Envio Gratis, - Programa Ahora 12
   
   d. Filtrar por precio '0 hasta 60.000'
   
   e. Ordenar por 'Menor precio'
   
OBSERVAR que los dos ultimos productos de la lista NO ESTAN ordenados por precio ($29482 y $41761)

4. Resultado esperado: que los productos de la lista esten ordenados de MENOR A MAYOR, en el rango de $0 a $60.000
   
5. Resultado actual: productos ordenados de menor a mayor SALVO los dos ultimos productos de la lista ($29482 y $41761)
   
6. Prueba visual: checkear link https://listado.mercadolibre.com.ar/_CostoEnvio_Gratis_TiempoEnvio_EnElDia_OrderId_PRICE_PriceRange_0-60000_Deal_semana-del-repuesto-original_Installments_CampaignAhora_NoIndex_True?button=
    
8. Severidad/Prioridad: Utilizando el sistema de Fibonacci, otorgo el puntaje de 8 a este bug (baja prioridad / bajo impacto), ya que no detiene el proceso de compra, y de acuerdo al monitoreo de clientes efectuado por Salesforce, un bajo porcentaje de usuarios utiliza estos filtros

BDD:
Given I am a mercadolibre.com.ar user
When I click on link for 35% offer
AND
When I filter products with price lower to higher
Then the products are not correctly filtered

Fin respuesta 1.1

---------------------------------------------------------------------------------------------------------------	
					
1.2 Ejercicio 2: Automatización de una web 
Debes realizar una automatización consistente en:

- Buscar en Google la palabra “automatización”
Using python and Selenium, the code would be something like:
from selenium import webdriver
from selenium.webdriver.common.keys import Keys

# Path to Chrome WebDriver executable
webdriver_path = '/path/to/chromedriver'

# Create a new instance of the Chrome driver
driver = webdriver.Chrome(executable_path=webdriver_path)

# Open Google's homepage
driver.get('https://www.google.com')

# Find the search box using its name attribute value
search_box = driver.find_element('name', 'q')

# Type the word "automatización" in the search box
search_box.send_keys('automatización')

# Press Enter to perform the search
search_box.send_keys(Keys.RETURN)

# Wait for a few seconds to see the results
driver.implicitly_wait(5)

# for result in search_results:
#     print(result.text)

# Close the browser window
driver.quit()

- Buscar el link de la Wikipedia resultante
Again, using python and selenium, this link search would be something like:

# Locate the Wikipedia link in the search results (assuming it's the first result)
wikipedia_link = driver.find_element_by_partial_link_text("Wikipedia")
wikipedia_link.click()
 						
- Comprobar en qué año se hizo el primer proceso automático
using python, and assuming requests beautifulsoup4 have been installed, it would be something like:
import requests
from bs4 import BeautifulSoup

def get_first_automated_test_date(search_term):
    # Wikipedia search URL
    search_url = f"https://es.wikipedia.org/wiki/{search_term}"

    # Send a GET request to the Wikipedia page
    response = requests.get(search_url)

    if response.status_code == 200:
        soup = BeautifulSoup(response.content, 'html.parser')

        # Find the first paragraph (or relevant section) containing the information about the automated test
        content_paragraphs = soup.find_all('p')
        for paragraph in content_paragraphs:
            if "prueba automatizada" in paragraph.text.lower():
                # Extract the date or relevant information from the paragraph
                automated_test_date = paragraph.text
                return automated_test_date.strip()

    return "Information about the first automated test not found on the Wikipedia page."

# Search term
search_term = "automatización"

# Get the first automated test date
automated_test_date = get_first_automated_test_date(search_term)

# Print the result
print("Result:")
print(automated_test_date)
 						
- Realizar un screenshot de la página de la Wikipedia
using python, and use the pyautogui library to take a screenshot of the search result
Would be something like:
import requests
from bs4 import BeautifulSoup
import pyautogui

# Wikipedia search URL
search_url = "https://es.wikipedia.org/wiki/Especial:Buscar"

# Search query
search_query = "automatización"

# Send a GET request to the Wikipedia search page
response = requests.get(search_url, params={'search': search_query})

# Parse the HTML content of the search result page
soup = BeautifulSoup(response.text, 'html.parser')

# Find the first search result link
search_result = soup.find('li', class_='mw-search-result')

if search_result:
    # Extract the URL of the search result
    result_url = "https://es.wikipedia.org" + search_result.a['href']
    
    # Open the search result page
    result_page = requests.get(result_url)
    result_soup = BeautifulSoup(result_page.text, 'html.parser')
    
    # Find the main content area
    content_div = result_soup.find('div', {'id': 'mw-content-text'})
    
    # Scroll to the content area
    pyautogui.click(x=50, y=50)  # Click on the top-left corner to focus the window
    pyautogui.scroll(-10)  # Scroll up to ensure the content area is visible
    
    # Take a screenshot of the content area
    content_area = content_div.get('id', '')
    screenshot_path = f"screenshot_{content_area}.png"
    pyautogui.screenshot(screenshot_path, region=(0, 0, 1920, 1080))  # Adjust region based on your screen resolution
    
    print(f"Screenshot saved as '{screenshot_path}'")
else:
    print(f"No search results found for '{search_query}' on Wikipedia.")
 						
- La resolución del ejercicio debe estar dentro de un repositorio de control de versiones para que podamos valorar arquitectura y codificación.
 						
---------------------------------------------------------------------------------------------------------------					 					


1.3 Ejercicio 3: Tratamiento de datos en APIs En este enlace encontrarás la documentación de la API de una tienda de mascotas:
					
https://petstore.swagger.io/
					
- Crea tu usuario mediante petición HTTP y posteriormente recupera sus datos llamando al servicio correspondiente.

utilizando el endpoint POST /user/createWithArray, envio el siguiente request (mejora: crear usuario en forma ordenada)

[
  {
    "id": 0,
    "username": "string",
    "firstName": "string",
    "lastName": "string",
    "email": "string",
    "password": "string",
    "phone": "string",
    "userStatus": 0
  }
]

Para recuperar datos, utilizo el endpoint GET /user/{username}, mediante el siguiente request

{
  "id": 0,
  "username": "string",
  "firstName": "string",
  "lastName": "string",
  "email": "string",
  "password": "string",
  "phone": "string",
  "userStatus": 0
}

       
- Recoge mediante petición HTTP, el JSON que retorna el endpoint /pet/findByStatus y lista mediante una función los nombres de las mascotas que se hayan vendido.

el JSON que retorna el endpoint es:
[
  {
    "id": 0,
    "category": {
      "id": 0,
      "name": "string"
    },
    "name": "doggie",
    "photoUrls": [
      "string"
    ],
    "tags": [
      {
        "id": 0,
        "name": "string"
      }
    ],
    "status": "available"
  }
]

el nombre de las mascotas que se vendieron, listadas mediante funcion, se consigue utilizando el endpoint GET pet/findByStatus, y en el Request se agrega lo siguiente:
[
  {
    "id": 0,
    "category": {
      "id": 0,
      "name": "string"
    },
    "name": "doggie",
    "photoUrls": [
      "string"
    ],
    "tags": [
      {
        "id": 0,
        "name": "string"
      }
    ],
    "status": "sold"
  }
]
       
-  El formato de salida deberá estar formado por la tupla {id, name}.
									
-  Puedes utilizar la estructura de datos que prefieras.
 													 						
- Crea una clase cuyo constructor requiera de la estructura de datos anterior y realiza un método que pueda recorrerla para poder identificar cuantas mascotas se llaman igual.
using python, would be something like:

import requests

class PetStoreAPI:
    def __init__(self, base_url='https://petstore.swagger.io/v2'):
        self.base_url = base_url

    def get_pet_count_by_name(self, pet_name):
        endpoint = f'{self.base_url}/pet/findByStatus'
        params = {'status': 'available'}  # adjust the status based on requirements
        response = requests.get(endpoint, params=params)

        if response.status_code == 200:
            pets = response.json()
            matching_pets = [pet for pet in pets if pet['name'] == pet_name]
            return len(matching_pets)
        else:
            return None

# Example usage
if __name__ == "__main__":
    pet_store = PetStoreAPI()

    pet_name = input("Enter the pet name to search: ")
    pet_count = pet_store.get_pet_count_by_name(pet_name)

    if pet_count is not None:
        print(f"There are {pet_count} pets with the name '{pet_name}'.")
    else:
        print("Failed to retrieve data from the Pet Store API.")

								 									
-  Ejemplo de salida: {“William”: 11, “ Floyd”: 2} Como output, te pediremos el código (puedes
 									
separarlo en archivos como quieras) y los resultados de salida de los puntos anteriores.
 								
								 									
-  Recuerda que puedes utilizar el lenguaje que prefieras y cualquier mejora adicional será bien considerada
 									
La resolución del ejercicio debe estar dentro de un repositorio de control de versiones para que podamos valorar arquitectura y codificación. 
