# Plate Number Detection

## About
This notebook contains code to detect plate number. The input is image file that contains plate number. The output is data that can be retrieved from the plate number. 

The following is description of the response:
|        Field Name         | Description                                                                                                                                                      |
|---------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `plat_no`                 | The plate number                                                                                                                                                 |
| `vehicle_color`           | Color of the vehicle                                                                                                                                             |
| `plate_color`             | Plate number color (background and foreground)                                                                                                                   |
| `area`                    | Plate area based on the prefix (Indonesian number plate format). Refer to Regulation of the Chief of the Indonesian National Police Number 7 of 2021             |
| `sub_area`                | Plate area based on the prefix and postfix (Indonesian number plate format). Refer to Regulation of the Chief of the Indonesian National Police Number 7 of 2021 |
| `vehicle_type_1`          | Vehicle type based on number segment. Refer to Regulation of the Chief of the Indonesian National Police Number 7 of 2021                                        |
| `vehicle_type_2`          | Vehicle type based on plate color. Refer to Regulation of the Chief of the Indonesian National Police Number 7 of 2021                                           |
| `plate_expired`           | Expired date for plate                                                                                                                                           |
| `is_expired`              | `true`/`false`. Calculate from the expire date and current date                                                                                                  |


Sample response:
```json
{
    "plat_no": "B 1481 TUB",
    "vahicle_color": "light blue",
    "plate_color": "yellow and black",
    "area": "Jakarta Raya",
    "sub_area": "Jakarta Utara",
    "vehicle_type_1": "Passenger Car",
    "vehicle_type_2": "Private or Rental Vehicle",
    "plate_expired": "June 2027",
    "is_expired": false,
    "gate_open": "N/A",
    "gate_closed": "N/A"
}
```

The following is the response when the image does not contain image:
```json
{
    "message": "The image does not contain vehicle",
}
```

## Run the .ipynb notebook
1. Start run from this line:
    ```
    !pip install -q -U google-generativeai python-dotenv
    ```
2. On the **Initialization** section, run one of section **Run in Google Collab** or **Run In Local** section. Depend on the environment you are working in. If you **Run in Google Collab**, set the key in the **secrets**. If you **Run In Local**, rename file `.env.example` to `.env` then insert your API Key. 
3. Continue run the next cell
4. on **Load File** section, select which image you want to detect. Change variable `vehicle_to_analyze` accordingly. 
5. Continue run the next cell to get the json file. 

## Experiment
### 1 - Taxi
Input:

![alt](./taxi.jpg)

Output:

![alt](./img_md/taxi_response.png)

### 2 - Bike
Input:

![alt](./bike_cirebon.png)

Output:

![alt](./img_md/bike_response.png)

### 3 - Car
Input:

![alt](./car_jakarta.jpg)

Output:

![alt](./img_md/car_response.png)

### 3 - Government Plate Number
Input:

![alt](./government.png)

Output:

![alt](./img_md/government_response.png)

### 4 - Not a Vehicle
Input:

![alt](./orang_utan.jpeg)

Output:

![alt](./img_md/orangutan_response.png)