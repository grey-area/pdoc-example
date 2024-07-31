# Use an official Python runtime as a parent image
FROM python:3.9-slim

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy the parent directory contents into the container at /usr/src/app
COPY . /usr/src/app

# Install any needed packages specified in requirements.txt
RUN pip install --upgrade pip && \
    pip install pdoc

# Define environment variable
ENV PATH="/usr/src/app/venv/bin:$PATH"

# The following command generates the documentation for the package in the root directory
# (we don't need to know the package name).
#CMD pdoc $(find . -type f -name "__init__.py" -exec dirname {} \; | head -n 1) -o docs/

# CMD, print the contents of the current directory
CMD ls -l