# PUT /surfreport/{id}

Replaces an existing surf report or creates it if it does not exist.

## Path Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| id | string | The unique identifier for the surf report you want to replace. Valid `id` values are returned when creating a surf report via POST. |

## Request Body Parameters

| Field | Required / Optional | Type | Description |
|-------|---------------------|------|-------------|
| beach | Required | string | Name of the beach. |
| {day} | Required | object | The day of the week for the surf report (e.g., `monday`). |
| {day}/{time} | Required | object | The hour for the conditions (e.g., `1pm`). |
| {day}/{time}/tide | Required | integer | The tide level at the beach. Tide is the distance inland that the water rises to, and can be a positive or negative number. When the tide is out, the number is negative. When the tide is in, the number is positive. The 0 point reflects the transition between the two states. |
| {day}/{time}/wind | Required | integer | The wind speed at the beach, measured in knots (nautical miles per hour). Wind speeds above 15 knots make surf conditions undesirable due to white caps and choppy water. |
| {day}/{time}/watertemp | Required | integer | The temperature of the water, in Fahrenheit or Celsius depending on the `units` parameter. Temperatures below 70°F typically require a wetsuit. Below 60°F, at least a 3mm wetsuit and booties are recommended. |
| {day}/{time}/surfheight | Required | integer | The height of the waves, in feet or centimeters depending on the `units` parameter. A surf height of 3 feet is the minimum size needed for surfing. If surf height exceeds 10 feet, it is not safe to surf. |

## Sample Request

```bash
curl -X PUT "https://api.openweathermap.org/data/2.5/surfreport/abc-456?appid=APIKEY" \
-H "Content-Type: application/json" \
-d '{
    "beach": "Santa Cruz",
    "monday": {
        "1pm": {
            "tide": 3,
            "wind": 10,
            "watertemp": 58,
            "surfheight": 3
        }
    }
}'
```

(In the above code, replace `APIKEY` with your actual API key.)

## Sample Response

The following is a sample response from the `surfreport/{id}` endpoint:

```json
{
    "id": "abc-456",
    "surfreport": [
        {
            "beach": "Santa Cruz",
            "monday": {
                "1pm": {
                    "tide": 3,
                    "wind": 10,
                    "watertemp": 58,
                    "surfheight": 3,
                    "recommendation": "Surfing conditions are okay, not great."
                }
            }
        }
    ]
}
```

## Response Definitions

| Field | Type | Description |
|-------|------|-------------|
| id | string | The unique identifier for the surf report that was replaced or created. |
| surfreport | array | The top-level array containing the full replaced or created surf report object. |
| beach | string | The beach name provided in the request. |
| {day} | object | The day of the week for the surf report. |
| {day}/{time} | string | The hour for the conditions. |
| {day}/{time}/tide | integer | The tide level at the beach. Tide is the distance inland that the water rises to, and can be a positive or negative number. When the tide is out, the number is negative. When the tide is in, the number is positive. The 0 point reflects the transition between the two states. |
| {day}/{time}/wind | integer | The wind speed at the beach, measured in knots (nautical miles per hour). Wind speeds above 15 knots make surf conditions undesirable due to white caps and choppy water. |
| {day}/{time}/watertemp | integer | The temperature of the water, returned in Fahrenheit or Celsius depending on the `units` parameter. Temperatures below 70°F typically require a wetsuit. Below 60°F, at least a 3mm wetsuit and booties are recommended. |
| {day}/{time}/surfheight | integer | The height of the waves, returned in feet or centimeters depending on the `units` parameter. A surf height of 3 feet is the minimum size needed for surfing. If surf height exceeds 10 feet, it is not safe to surf. |
| {day}/{time}/recommendation | string | An overall recommendation based on wind, watertemp, and surfheight. Three possible values: `"Go surfing!"`, `"Surfing conditions are okay, not great."`, or `"Not a good day for surfing."` |

← Back to [API Home](../index.md)