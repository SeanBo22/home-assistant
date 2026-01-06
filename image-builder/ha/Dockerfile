FROM homeassistant/home-assistant:stable

# Prevent pip cache bloat
ENV PIP_NO_CACHE_DIR=1

# Install system build tools just in case (safe)
RUN apk add --no-cache \
    build-base \
    python3-dev

# Install Python deps globally into HA
COPY requirements.txt /tmp/requirements.txt
RUN pip install --no-deps -r /tmp/requirements.txt
