FROM python:3.13-bullseye AS builder

WORKDIR /builder

RUN python -m pip install --upgrade pip setuptools
RUN pip install wheel cython pyinstaller
COPY . .
RUN cp ./pkg/solid.spec solid.spec
RUN pip install -r requirements.txt
RUN pyinstaller solid.spec

FROM scratch

COPY --from=builder /builder/dist/solid /solid