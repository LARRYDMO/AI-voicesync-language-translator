
# Audio Translation Service

This project is a Flask-based web application that provides audio translation services. Users can upload an audio file in one language, and the application will recognize the speech, translate it to another language, and return the translated audio.

## Features

- Speech recognition using Google Speech Recognition.
- Translation using Google Translate API.
- Text-to-speech conversion using gTTS (Google Text-to-Speech).
- Supports multiple languages for both input and output.
- Provides a RESTful API for easy integration.

## Requirements

- Python 3.7+
- Flask
- SpeechRecognition
- gTTS
- deep_translator
- pydub
- flask_cors
- werkzeug

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/LARRYDMO/Language_translation.git
   cd audio-translation-service
   ```

2. Create a virtual environment:

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. Install the required packages:

   ```bash
   pip install -r requirements.txt
   ```

4. Create the `uploads` directory:

   ```bash
   mkdir uploads
   ```

## Usage

1. Start the Flask server:

   ```bash
   python main.py
   ```

2. Use an API client (like Postman) or a web browser to interact with the service.

### API Endpoints

- **POST /start_translation**

  Starts the translation service with specified input and output languages.

  Request Body:
  ```json
  {
    "input_lang": "en",
    "output_lang": "es"
  }
  ```

  Response:
  - `200 OK` with translated audio.
  - `400 Bad Request` if languages are not specified.
  - `500 Internal Server Error` if an error occurs during translation.

- POST /stop_translation

  Stops the translation service.

  Response:
  - `200 OK` if the service is stopped successfully.
  - `400 Bad Request` if the service is not running.

- POST /translate

  Translates an uploaded audio file.

  Form Data:
  - `lang_one`: Source language (e.g., `en`).
  - `lang_two`: Target language (e.g., `es`).
  - `record`: Audio file to be translated.

  Response:
  - `200 OK` with translated audio.
  - `400 Bad Request` if parameters are missing.
  - `500 Internal Server Error` if an error occurs during translation.

- GET /translated_audio/<filename>

  Downloads the translated audio file.

## Example

### Translating an Audio File

1. Send a POST request to `/translate` with the audio file and language parameters.

   Example using `curl`:
   ```bash
   curl -X POST -F "lang_one=en" -F "lang_two=es" -F "record=@path/to/your/audiofile.mp3" http://127.0.0.1:5000/translate
   ```

2. The translated audio file will be returned in the response.

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request with your changes. Ensure that your code adheres to the existing style and includes appropriate tests.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgements

- [Flask](https://flask.palletsprojects.com/)
- [Google Speech Recognition](https://pypi.org/project/SpeechRecognition/)
- [gTTS (Google Text-to-Speech)](https://pypi.org/project/gTTS/)
- [deep_translator](https://pypi.org/project/deep-translator/)
- [pydub](https://pypi.org/project/pydub/)
- [flask_cors](https://pypi.org/project/Flask-Cors/)
- [werkzeug](https://pypi.org/project/Werkzeug/)

## Contact

For any questions or suggestions, please feel free to contact [LARRYDMO](mailto:yourname@example.com).
