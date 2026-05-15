# DELETE /surfreport/{id}

Deletes a surf report for a specific beach.

## Path Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| id | string | The unique identifier for the surf report you want to delete. Valid `id` values are returned when creating a surf report via POST. |

## Sample Request

```bash
curl -X DELETE "https://api.openweathermap.org/data/2.5/surfreport/abc-456?appid=APIKEY"
```

(In the above code, replace `APIKEY` with your actual API key.)

## Sample Response

The following is a sample response from the `surfreport/{id}` endpoint:

```json
{
  "id": "abc-456"
}
```

## Response Definitions

| Field | Type | Description |
|-------|------|-------------|
| id | string | The unique identifier for the surf report that was deleted. |

← Back to [API Home](../index.md)