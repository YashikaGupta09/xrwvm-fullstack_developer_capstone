FROM python:3.12.0-slim-bookworm

ENV PYTHONBUFFERED 1
ENV PYTHONWRITEBYTECODE 1
ENV APP=/app

# Set working directory
WORKDIR $APP

# Copy requirements
COPY requirements.txt $APP

# Install dependencies
RUN pip3 install --upgrade pip
RUN pip3 install -r requirements.txt

# Copy project files
COPY . $APP

# Expose Django port
EXPOSE 8000

# Make entrypoint executable
RUN chmod +x /app/entrypoint.sh

# Run entrypoint
ENTRYPOINT ["/bin/bash","/app/entrypoint.sh"]

# Start server
CMD ["gunicorn", "--bind", ":8000", "--workers", "3", "djangoproj.wsgi"]