# Surf Report API Documentation

The Surf Report API provides surf conditions for beaches, including wave height, wind speed, water temperature, tide levels, and recommendations.

## Base URL

https://api.openweathermap.org

---

## Available Endpoints

### GET /surfreport/{beachId}

Retrieves surf conditions for a specific beach.

[View Documentation](surfreport/get.md)

---

### POST /surfreport

Creates a new surf report.

[View Documentation](surfreport/post.md)

---

### PUT /surfreport/{beachId}

Replaces an existing surf report or creates it if it does not exist.

[View Documentation](surfreport/put.md)

---

### PATCH /surfreport/{beachId}

Partially updates an existing surf report.

[View Documentation](surfreport/patch.md)

---

### DELETE /surfreport/{beachId}

Deletes a surf report for a specific beach.

[View Documentation](surfreport/delete.md)

---

## Notes

- All responses are returned in JSON format
- All timestamps use UTC
- Units may be set to imperial or metric
- Each endpoint includes sample requests, responses, and response definitions