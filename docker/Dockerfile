# Use a Python image to create a virtual environment
FROM python:3.9 as builder

WORKDIR $GITHUB_WORKSPACE/app

# Add required files (assuming 'app' directory contains all necessary files)
ADD $GITHUB_WORKSPACE/app /app

# Create and activate a virtual environment
RUN python3 -m venv /venv
ENV PATH="/venv/bin:$PATH"

# Install dependencies within the virtual environment
RUN /venv/bin/pip install --no-cache-dir -r /app/requirements.txt

# Use the distroless/python3 base image
#FROM gcr.io/distroless/python3:debug-nonroot

# # Copy only the necessary components from the builder image
# COPY --from=builder /venv /venv
# COPY --from=builder /app /app

# Set the working directory inside the container
WORKDIR /app

# Expose the port that your application listens on
EXPOSE 5000

# Specify the command to run on container start
CMD ["/venv/bin/python", "/app/main.py"]
