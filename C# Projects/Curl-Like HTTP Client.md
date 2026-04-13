# Vala Project Idea: Curl-Like HTTP Client
## Project Name

vurl – A lightweight curl-like HTTP client written in Vala.

## Overview

This project involves building a command-line HTTP client similar to curl. The goal is to create a simple yet powerful tool capable of sending HTTP requests, displaying responses, and interacting with web APIs. It serves as an excellent exercise in systems programming, networking, and CLI design using Vala.

The project emphasizes clean architecture, modular design, and incremental feature development.

## Objectives
Build a fully functional HTTP client using Vala.
Gain experience with command-line argument parsing.
Learn to interact with web services using libsoup.
Handle HTTP methods, headers, and payloads.
Implement file handling and structured error management.
Develop a production-quality CLI tool with extensible architecture.

## Features
Core Features
Perform HTTP GET requests.
Send HTTP requests using custom methods (POST, PUT, DELETE, PATCH).
Attach custom request headers.
Send request bodies, including JSON payloads.
Display HTTP status codes and response headers.
Save responses to files.
Handle errors gracefully with meaningful exit codes.
Supported Command Examples
vurl https://example.com
vurl -i https://example.com
vurl -X POST https://httpbin.org/post -d "hello"
vurl -H "Content-Type: application/json" -d '{"name":"Rudi"}' https://httpbin.org/post
vurl --status-only https://example.com
vurl -o response.txt https://example.com

## Feature Roadmap
Milestone	Feature	Description
1	Basic GET	Fetch and print the response body.
2	Status & Headers	Display HTTP status codes and headers.
3	Custom Methods	Support -X for specifying HTTP methods.
4	Request Headers	Add support for custom headers using -H.
5	Request Body	Send request data with -d or --json.
6	File Output	Save responses using -o.
7	Error Handling	Provide meaningful error messages and exit codes.


## Project Structure
vurl/
├── src/
│   ├── main.vala
│   ├── cli.vala
│   ├── request_options.vala
│   ├── http_client.vala
│   ├── output_writer.vala
│   └── header_parser.vala
├── meson.build
├── README.md
└── LICENSE
File Responsibilities
File	Purpose
main.vala	Application entry point and orchestration.
cli.vala	Command-line argument parsing and validation.
request_options.vala	Data model representing HTTP request configuration.
http_client.vala	HTTP communication using libsoup.
output_writer.vala	Handles stdout and file output.
header_parser.vala	Parses and validates header input.

## Technology Stack
Component	Technology
Language	Vala
HTTP Library	libsoup
Build System	Meson
CLI Execution	GLib
Platform Support	Linux, Windows*, macOS

* Windows support requires a GTK/libSoup environment such as MSYS2.


## Dependencies
Vala
GLib
libsoup
Meson
Ninja


## Expected Command-Line Options
Option	Description
-X METHOD	Specify the HTTP method.
-H "Key: Value"	Add a custom request header.
-d DATA	Send raw request data.
--json DATA	Send JSON data with the appropriate content type.
-i	Include response headers in output.
--status-only	Print only the HTTP status code.
-o FILE	Save the response body to a file.
--timeout SECONDS	Specify request timeout.
-v	Enable verbose output.
-L	Follow redirects.

## Exit Codes
Code	Meaning
0	Success
1	Invalid command-line usage
2	Network or request failure
3	File write error

## Testing Endpoints
Purpose	URL
Basic Request	https://example.com

JSON API	https://api.github.com

POST Testing	https://httpbin.org/post

Status Codes	https://httpbin.org/status/404

Headers Echo	https://httpbin.org/headers

Delayed Response	https://httpbin.org/delay/3

## Stretch Goals
Follow HTTP redirects (-L).
Verbose debug output (-v).
Custom User-Agent support.
Multipart form uploads.
Pretty-print JSON responses.
Colored terminal output.
HEAD request support.
Timeout configuration.
Cookie handling.
Proxy support.
HTTP/2 enhancements.

## Development Milestones
Milestone 1 – Minimal Client
Parse URL.
Perform a GET request.
Print the response body.
Milestone 2 – Enhanced Output
Add status code and header display.
Milestone 3 – Full Request Control
Implement custom methods, headers, and request bodies.
Milestone 4 – File Output and Stability
Enable file output and robust error handling.
Milestone 5 – Advanced Features
Add verbose mode, redirects, and timeout controls.

## Learning Outcomes

By completing this project, you will gain experience in:

Systems programming with Vala.
Building command-line tools.
Consuming HTTP APIs.
Working with GLib and libsoup.
Designing modular and maintainable applications.
Implementing robust error handling and file I/O.
Using Meson for cross-platform builds.

## License

This project is intended for educational and open-source use. You may license it under the MIT License.

## Inspiration

This project is inspired by the functionality and simplicity of the curl command-line tool, reimagined in Vala as a lightweight and educational systems programming exercise.
