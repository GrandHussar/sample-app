FROM python:3.9-slim
WORKDIR /home/myapp

# Add missing GPG keys for Debian bookworm
RUN apt-get update && apt-get install -y --no-install-recommends gnupg &&     apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0E98404D386FA1D9 6ED0E7B82643E131 F8D2585B8783D481 54404762BBB6E853 BDE6D2B9216EC7A8 &&     rm -rf /var/lib/apt/lists/*

# Install necessary system packages
RUN apt-get update && apt-get install -y --no-install-recommends     build-essential     libssl-dev     libffi-dev     python3-dev     && rm -rf /var/lib/apt/lists/*

# Upgrade pip and disable progress bar
RUN pip install --upgrade pip --no-cache-dir --progress-bar=off

# Install Flask and disable progress bar
RUN pip install flask --no-cache-dir --progress-bar=off

COPY ./static /home/myapp/static
COPY ./templates /home/myapp/templates
COPY sample_app.py /home/myapp

EXPOSE 5050
CMD ["python", "/home/myapp/sample_app.py"]
