# GET /surfreport

Returns surf conditions for a specific beach.

## Query Parameters

| Parameter | Required / Optional | Type | Description |
|-----------|---------------------|------|-------------|
| zip | Required | integer | The zip code for the beach location you want to look up. |
| days | Optional | integer | Number of forecast days to return. Default is 3. Maximum is 7. |
| time | Optional | integer | If included, only the conditions for that hour are returned. Unix format (ms since 1970) in UTC. |
| units | Optional | string | Measurement system (`imperial` or `metric`). |

## Sample Request

```bash
curl -I -X GET "https://api.openweathermap.org/data/2.5/surfreport?zip=95050&appid=APIKEY&units=imperial&days=2"
```

(In the above code, replace `APIKEY` with your actual API key.)

## Sample Response

The following is a sample response from the `surfreport` endpoint:

```json
{
    "surfreport": [
        {
            "beach": "Santa Cruz",
            "monday": {
                "1pm": {
                    "tide": 5,
                    "wind": 15,
                    "watertemp": 60,
                    "surfheight": 5,
                    "recommendation": "Go surfing!"
                }
            }
        }
    ]
}
```

## Response Definitions

| Field | Type | Description |
|-------|------|-------------|
| surfreport | array | The top-level array containing surf report objects for each beach returned. |
| beach | string | The beach name corresponding to the zip code in the request. |
| {day} | object | The day of the week for the forecast. A maximum of 3 days is returned unless otherwise specified with the `days` parameter. |
| {day}/{time} | string | The hour for the conditions. This item is included only if you include a `time` parameter in the request. |
| {day}/{time}/tide | integer | The tide level at the beach. Tide is the distance inland that the water rises to, and can be a positive or negative number. When the tide is out, the number is negative. When the tide is in, the number is positive. The 0 point reflects the transition between the two states. |
| {day}/{time}/wind | integer | The wind speed at the beach, measured in knots (nautical miles per hour). Wind speeds above 15 knots make surf conditions undesirable due to white caps and choppy water. |
| {day}/{time}/watertemp | integer | The temperature of the water, returned in Fahrenheit or Celsius depending on the `units` parameter. Temperatures below 70°F typically require a wetsuit. Below 60°F, at least a 3mm wetsuit and booties are recommended. |
| {day}/{time}/surfheight | integer | The height of the waves, returned in feet or centimeters depending on the `units` parameter. A surf height of 3 feet is the minimum size needed for surfing. If surf height exceeds 10 feet, it is not safe to surf. |
| {day}/{time}/recommendation | string | An overall recommendation based on wind, watertemp, and surfheight. Three possible values: `"Go surfing!"`, `"Surfing conditions are okay, not great."`, or `"Not a good day for surfing."` |

← Back to [API Home](../index.md)