# SurfReport API Documentation

This is a mock API documentation sample built as a practice exercise for documenting REST API endpoints. It is modeled after the [OpenWeatherMap API](https://openweathermap.org/api).

## About This Project

The SurfReport API is a fictional extension of the OpenWeatherMap API that returns surf conditions for a specific beach, including wave height, wind speed, water temperature, tide level, and an overall surf recommendation.

This project documents five REST endpoints using a consistent structure for each: a resource description, parameters, a sample request, a sample response, and response definitions.

## Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /surfreport | Returns surf conditions for a specific zip code. |
| POST | /surfreport | Creates a new surf report. |
| PUT | /surfreport/{id} | Replaces an existing surf report or creates it if it does not exist. |
| PATCH | /surfreport/{id} | Partially updates an existing surf report. |
| DELETE | /surfreport/{id} | Deletes a surf report for a specific beach. |

## Tools Used

- [Jekyll](https://jekyllrb.com/) — static site generator
- [GitHub Pages](https://pages.github.com/) — hosting

## Course Reference

This project was completed as part of the Hackmamba Creator Community's Week 3 exercise for the [Documenting APIs](https://idratherbewriting.com/learnapidoc/) course by Tom Johnson.
