FROM python:3.9-slim

# Set the working directory
WORKDIR /app

# Install Python dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Create a non-root user
RUN useradd --create-home appuser

# Copy the application files
COPY . .

# Set ownership and switch to the non-root user
RUN chown -R appuser:appuser /app
USER appuser

# Configure the application
ENV FLASK_APP=service
ENV PYTHONUNBUFFERED=1

# Expose the service port
EXPOSE 8080

# Start the service
CMD ["flask", "run", "--host=0.0.0.0", "--port=8080"]
