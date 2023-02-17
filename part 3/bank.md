## Dockerfile

this file is placed at the root directory

<div>

```Dockerfile
FROM python:3.10-alpine

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

WORKDIR /usr/src/bank
COPY bank/* ./bank/
COPY templates/* ./templates/
COPY wp_bank/* ./wp_bank/
COPY manage.py ./
COPY db.sqlite3 ./

EXPOSE 8000
RUN pip3 install django djangorestframework  # Use pip3 in linux and macOS

RUN python3 manage.py migrate
CMD ["python3", "manage.py", "runserver", "0.0.0.0:8000"]
```

</div>

## command

sudo docker build . -t shahab/bank
sudo docker run -p 8000:8000 shahab/bank