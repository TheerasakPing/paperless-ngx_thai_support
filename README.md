# Paperless-NGX with Thai Language Support

This repository provides a customized `docker-compose.yml` file for running [Paperless-NGX](https://github.com/paperless-ngx/paperless-ngx) with support for Thai and English OCR.

## Features
- Uses PostgreSQL instead of SQLite for better performance.
- Supports Thai (`tha`) and English (`eng`) OCR.
- Includes Apache Tika and Gotenberg for processing Office documents.
- Stores Paperless data in a custom directory (`E:\paperless`).

## Installation
### Prerequisites
Ensure you have the following installed:
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Git](https://git-scm.com/)

### Setup Instructions
1. **Clone the repository:**
   ```sh
   git clone https://github.com/ArLiw317/paperless-ngx_thai_support.git
   cd paperless-ngx_thai_support
   ```

2. **Pull Docker images:**
   ```sh
   docker compose pull
   ```

3. **Create a superuser for Paperless:**
   ```sh
   docker compose run --rm webserver createsuperuser
   ```

4. **Start Paperless:**
   ```sh
   docker compose up -d
   ```

5. **Access Paperless:**
   Open your browser and go to:  
   [http://localhost:8001](http://localhost:8001)

## Storage Configuration
Paperless stores its files in `E:\paperless`. If you want to change the location, update the `docker-compose.yml` file:
```yaml
volumes:
  - E:\your_custom_path\data:/usr/src/paperless/data
  - E:\your_custom_path\media:/usr/src/paperless/media
  - E:\your_custom_path\export:/usr/src/paperless/export
  - E:\your_custom_path\consume:/usr/src/paperless/consume
```

## Troubleshooting
- If OCR for Thai does not work, make sure `tesseract-ocr-tha` is installed inside the container.
- To check logs, use:
  ```sh
  docker compose logs -f webserver
  ```

## Contributing
Feel free to submit issues or pull requests to improve this repository!

## License
This project is open-source under the MIT License.

