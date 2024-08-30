# rabbit-dedup-delay-shovel

A preconfigured RabbitMQ Docker image with essential plugins for message deduplication, delayed message exchange, and shoveling, designed for the development needs of the DataHubs Team at Hoffmann Group.

## Overview

This Docker image extends the official RabbitMQ management image with the following plugins:

- **rabbitmq_delayed_message_exchange**: Allows delayed message processing.
- **rabbitmq_message_deduplication**: Prevents duplicate messages from being processed.
- **rabbitmq_shovel**: Enables message forwarding between different brokers.
- **rabbitmq_shovel_management**: Provides management features for the Shovel plugin.

These plugins are integrated to enhance RabbitMQ's capabilities in a development environment where message reliability and timing are critical.

## Features

- **Preconfigured RabbitMQ**: The image comes with the necessary plugins already installed and enabled.
- **Delayed Message Exchange**: Schedule message deliveries with precision.
- **Message Deduplication**: Ensure that only unique messages are processed.
- **Message Shoveling**: Seamlessly forward messages between RabbitMQ instances.

## How to Use

### Pull the Image

You can pull the prebuilt Docker image from the GitHub Container Registry:

```bash
docker pull ghcr.io/hoffmann-dsd/rabbit-dedup-delay-shovel:latest
```

Alternatively, specify a version:

```bash
docker pull ghcr.io/hoffmann-dsd/rabbit-dedup-delay-shovel:3.11.0
```

### Build the Image Yourself

To build the image from this repository, clone the repo and run:

```bash
git clone https://github.com/hoffmann-dsd/rabbit-dedup-delay-shovel.git
cd rabbit-dedup-delay-shovel
docker build -t rabbit-dedup-delay-shovel:latest .
```

### Run the Container

Once you have the image, you can run it using Docker:

```bash
docker run -d \
    -p 5672:5672 \
    -p 15672:15672 \
    --name rabbitmq-custom \
    rabbit-dedup-delay-shovel:latest
```

### Access the RabbitMQ Management UI

The RabbitMQ Management UI will be available at [http://localhost:15672](http://localhost:15672). The default credentials are:

- Username: `guest`
- Password: `guest`

## Configuration

The image includes a default `rabbitmq.conf` file, which can be customized to suit your specific requirements. To use your configuration file, mount it as a volume when running the container:

```bash
docker run -d \
    -p 5672:5672 \
    -p 15672:15672 \
    -v /path/to/your/rabbitmq.conf:/etc/rabbitmq/rabbitmq.conf \
    --name rabbitmq-custom \
    rabbit-dedup-delay-shovel:latest
```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request.
