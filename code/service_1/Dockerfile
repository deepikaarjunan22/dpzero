FROM golang:tip-alpine3.22
COPY go.mod ./
RUN go mod download 
COPY . .
RUN go build -o main main.go
EXPOSE 8080
CMD ["./main"] 
