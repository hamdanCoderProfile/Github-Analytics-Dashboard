FROM python:3.8.18

# Set environment variables
ENV PORT=8080
ENV HOSTDIR=0.0.0.0

# Install necessary packages and update pip
# RUN apt-get update -y && apt-get install -y python3-pip && pip install --upgrade pip

RUN apt-get update && apt-get install -y \
    build-essential \
    python3-dev \
    libhdf5-dev \
    && apt-get clean

# Install Python dependencies
COPY requirements.txt .
RUN pip install --upgrade pip \
    && pip install -r requirements.txt

# Set the working directory
WORKDIR /app

# Copy requirements.txt first to leverage Docker caching
# Install Python dependencies
# Copy the rest of the application code
COPY . /app

# Expose the port and set the default command
EXPOSE 8080
CMD ["python", "app.py"]



ENTRYPOINT ["python", "app.py"]



