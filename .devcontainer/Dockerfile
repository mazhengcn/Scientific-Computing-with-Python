FROM python:slim-bullseye AS base

FROM base AS pip-installs
ARG VENV_PATH

RUN python -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"

COPY requirements.txt /tmp/pip-tmp/
RUN pip install --upgrade --no-cache-dir pip \
    && pip install --no-cache-dir -r /tmp/pip-tmp/requirements.txt \
    && rm -rf /tmp/pip-tmp

FROM base
COPY --from=pip-installs /opt/venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"