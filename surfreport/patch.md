# PATCH /surfreport/{id}

Partially updates an existing surf report.

## Path Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| id | string | The unique identifier for the surf report you want to update. Valid `id` values are returned when creating a surf report via POST. |

## Request Body Parameters

Only include the fields you want to update.

| Field | Required / Optional | Type | Description |
|-------|---------------------|------|-------------|
| {day} | Required | object | The day of the week for the entry you want to update (e.g., `monday`). |
| {day}/{time} | Required | object | The hour for the entry you want to update (e.g., `1pm`). |
| {day}/{time}/tide | Optional | integer | The tide level at the beach. Tide is the distance inland that the water rises to, and can be a positive or negative number. When the tide is out, the number is negative. When the tide is in, the number is positive. The 0 point reflects the transition between the two states. |
| {day}/{time}/wind | Optional | integer | The wind speed at the beach, measured in knots (nautical miles per hour). Wind speeds above 15 knots make surf conditions undesirable due to white caps and choppy water. |
| {day}/{time}/watertemp | Optional | integer | The temperature of the water, in Fahrenheit or Celsius depending on the `units` parameter. Temperatures below 70°F typically require a wetsuit. Below 60°F, at least a 3mm wetsuit and booties are recommended. |
| {day}/{time}/surfheight | Optional | integer | The height of the waves, in feet or centimeters depending on the `units` parameter. A surf height of 3 feet is the minimum size needed for surfing. If surf height exceeds 10 feet, it is not safe to surf. |

## Sample Request

```bash
curl -X PATCH "https://api.openweathermap.org/data/2.5/surfreport/abc-456?appid=APIKEY" \
-H "Content-Type: application/json" \
-d '{
    "monday": {
        "1pm": {
            "wind": 18
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
                    "tide": 5,
                    "wind": 18,
                    "watertemp": 59,
                    "surfheight": 4,
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
| id | string | The unique identifier for the surf report that was partially updated. |
| surfreport | array | The top-level array containing the full updated surf report object. |
| beach | string | The beach name associated with the surf report. |
| {day} | object | The day of the week for the surf report. |
| {day}/{time} | string | The hour for the conditions. |
| {day}/{time}/tide | integer | The tide level at the beach. Tide is the distance inland that the water rises to, and can be a positive or negative number. When the tide is out, the number is negative. When the tide is in, the number is positive. The 0 point reflects the transition between the two states. |
| {day}/{time}/wind | integer | The wind speed at the beach, measured in knots (nautical miles per hour). Wind speeds above 15 knots make surf conditions undesirable due to white caps and choppy water. |
| {day}/{time}/watertemp | integer | The temperature of the water, returned in Fahrenheit or Celsius depending on the `units` parameter. Temperatures below 70°F typically require a wetsuit. Below 60°F, at least a 3mm wetsuit and booties are recommended. |
| {day}/{time}/surfheight | integer | The height of the waves, returned in feet or centimeters depending on the `units` parameter. A surf height of 3 feet is the minimum size needed for surfing. If surf height exceeds 10 feet, it is not safe to surf. |
| {day}/{time}/recommendation | string | An overall recommendation based on wind, watertemp, and surfheight. Three possible values: `"Go surfing!"`, `"Surfing conditions are okay, not great."`, or `"Not a good day for surfing."` |
| updatedFields | array | A list of the fields that were modified in the request (e.g., `["monday/1pm/wind"]`). |

← Back to [API Home](../index.md)