# 42 Get Next Line

Welcome to 42 Get Next Line! This project challenges you to create a function that reads a line from a file descriptor. The goal is to handle reading and parsing of multi-file descriptors and multi-line inputs.

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Usage](#usage)
4. [Build Commands](#build-commands)
5. [Contributing](#contributing)
6. [License](#license)

## Introduction

The `get_next_line` project requires you to implement a function that reads a line from a file descriptor and handles multiple file descriptors simultaneously. This function is useful for parsing data from files or other input streams.

## Getting Started

To get started with `get_next_line`, simply clone this repository to your local machine:

```bash
git clone https://github.com/T-001v2r3/get_next_line.git
```
Once you have the repository cloned, include the get_next_line.h header file in your project, and add the get_next_line.c file to your compilation command.
## Usage

Here's an example of how to use get_next_line in your project:

```c
#include "get_next_line.h"

int main() {
    int fd;
    char *line;

    fd = open("example.txt", O_RDONLY);
    while (get_next_line(fd, &line) > 0) {
        printf("%s\n", line);
        free(line);
    }
    close(fd);
    return 0;
}
```
This project also includes a bonus version of the function that can handle multiple file descriptors. Here's an example of how to use the bonus version:

```c
#include "get_next_line_bonus.h"

int main() {
	int fd1, fd2;
	char *line;

	fd1 = open("example1.txt", O_RDONLY);
	fd2 = open("example2.txt", O_RDONLY);
	while (get_next_line(fd1, &line) > 0 || get_next_line(fd2, &line) > 0) {
		printf("%s\n", line);
		free(line);
	}
	close(fd1);
	close(fd2);
	return 0;
}
```

In this example, the get_next_line function is used to read lines from two different files simultaneously.

## Build Commands

Use the following commands to build and clean your project:

```bash
gcc -Wall -Wextra -Werror -D BUFFER_SIZE=32 get_next_line.c get_next_line_utils.c main.c -o gnl # Standard version
gcc -Wall -Wextra -Werror -D BUFFER_SIZE=32 -D BONUS get_next_line_bonus.c get_next_line_utils_bonus.c main_bonus.c -o gnl_bonus # With bonus functions (multiple file descriptors)
```
Replace BUFFER_SIZE with the desired buffer size.
## Contributing

Contributions to get_next_line are welcome! If you have ideas for improvements, bug fixes, or additional features, feel free to open an issue or submit a pull request.
## License

This project is licensed under the terms of the MIT license.