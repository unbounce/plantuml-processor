# PlantUML Processor Docker Image

This project creates a docker image that knows how to process
[PlantUML](http://plantuml.sourceforge.net/) files in an 
inbox/outbox filing system.

An inbox/outbox filing system is an architecture from
[batch processing systems](http://en.wikipedia.org/wiki/Batch_processing)
where a batch job has pre-defined directory names to work with.  It
processes everything in an inbox, and sends the output into the outbox.
The docker image is then run with an ``/inbox`` and ``/outbox`` volumes
mounted.

## Getting Started

Use the docker image like so:

```
docker run \
       -v path/to/diagrams:/inbox \
       -v path/to/put/artifacts:/outbox \
       unbounce/plantuml-processor
```

where:
* ``path/to/diagrams`` points to a directory on your machine where the PlantUML diagram files kept.  They can be of any file type (PlantUML will look in each non-binary file for specific tags).
* ``path/to/put/artifacts`` points to a directory where the PlantUML PNG deliverables are stored.

## Building

Build the docker image based on the project's [Dockerfile](Dockerfile).

```
make
```

## Distributing

Push the docker image to Docker Hub.  You need write permissions into the
namespace given in the [Makefile](Makefile).

```
make dist
```

The docker image will be uploaded as ``unbounce/plantuml-processor``, or
as defined in the [Makefile](Makefile).

## Testing

Test this docker image out with the following.

```
make test
```

