# API Documentation - Process Image

This API endpoint allows processing of detected faces

## Endpoint
```
POST /process-image
```

## Description
This API processes an image stored in an S3 bucket and returns the processing result.

## Request Headers
```json
{
  "Content-Type": "application/json",
  "x-api-key": "<API_KEY>"
}
```

## Request Body
```json
{
  "payloadId": "<string>", // Unique identifier for the payload
  "timestamp": "<ISO8601 string>", // Timestamp indicating the time of the payload submission
  "s3Bucket": "<string>", // Name of the S3 bucket where the image is stored
  "imageLocation": "<string>", // Key of the image in the S3 bucket
  "imageFormat": "<string>", // Format of the image (e.g., jpg, png)
  "metadata": {
    "description": "<string>", // Optional description of the image
    "tags": ["<string>", "<string>"] // Array of tags or labels associated with the image
  },
  "requesterInfo": {
    "userId": "<string>", // ID of the user making the request
    "ipAddress": "<string>", // Optional IP address of the requester
    "department": "<string>" // Optional department or organization
  }
}
```

## Response

### 200 - Success
```json
{
  "payloadId": "<string>", // Same payload ID as the request
  "status": "success",
  "processedAt": "<ISO8601 string>", // Timestamp when the image was processed
  "details": "<string>" // Additional details about the processing
}
```

### 400 - Bad Request
```json
{
  "error": "<string>",
  "details": "<string>"
}
```

### 401 - Unauthorized
```json
{
  "error": "<string>",
  "details": "<string>"
}
```

### 500 - Internal Server Error
```json
{
  "error": "<string>",
  "details": "<string>"
}
```

## Notes
- The `x-api-key` header is required for authentication.
- Ensure that the S3 bucket and the provided image key are accessible.
- Use ISO8601 format for timestamps (e.g., `2023-01-01T12:00:00Z`).

## License
This project is licensed under the MIT License.
