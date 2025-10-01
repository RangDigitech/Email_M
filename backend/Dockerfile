# Use an official Python runtime as a parent image
FROM python:3.9-slim

# Set the working directory in the container
WORKDIR /app

# Copy the requirements file into the container at /app
COPY requirements.txt .

# Install any needed packages specified in requirements.txt
# Use --no-cache-dir to reduce image size
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the backend application code
COPY . .

# Expose the port Gunicorn will run on
EXPOSE 8000

# Command to run the application using Gunicorn
# Binds to 0.0.0.0:8000 to be accessible from outside the container
# --workers 4 specifies 4 worker processes to handle requests
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "--workers", "4", "app:app"]