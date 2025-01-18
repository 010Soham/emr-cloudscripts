FROM python:3.8

# Create a group and user
RUN groupadd -r appuser && useradd -r -g appuser appuser

WORKDIR /app

# Copy requirements.txt first
COPY requirements.txt ./

# Change ownership of the working directory
RUN chown -R appuser:appuser /app

# Switch to non-root user
USER appuser

# Upgrade pip
RUN python -m pip install --upgrade pip --user

# Install dependencies
RUN pip install --user -r requirements.txt

# Update PATH environment variable
ENV PATH="/home/appuser/.local/bin:${PATH}"

# Copy the rest of the application code
COPY . ./

# Run the application
CMD ["python", "your_script.py"]
