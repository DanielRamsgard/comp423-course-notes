# Setting up a dev container for Rust

* Primary author: [Daniel Ramsgard](https://github.com/DanielRamsgard)

### Prerequisites

#### Prerequisite Installations

1. Docker Desktop
2. VS Code
4. Git

#### Intellectual Prerequisites

1. Basic Knowledge of Rust Syntax
2. Basic Proficiency of Git Commands
3. Docker Mental Model

### Steps

#### Notice

The reader is expected to running the Bash shell whether they are on MacOS, Linux, or Windows.

#### Diretory Setup

1. Run the following command `mkdir <name>` to create a new project directory. Now, enter into that directory by executing `cd <name>`.
2. To create an empty Git directory, run `git init`.

#### Dev Container Configuration

1. Create a new directory called `.devcontainer` and enter into it with the run the following command `mkdir .devcontainer && cd .devcontainer` for MacOS, Linux, and Windows.
2. Create a new file within the `.devcontainer` directory with the following command `touch devcontainer.json`.
3. Paste the following into the `devcontainer.json` file: 
```json 
{
    "name": "<insert a desired name>",
    "image": "mcr.microsoft.com/devcontainers/rust:latest",
    "customizations": {
        "vscode": {
            "settings": {},
            "extensions": []
        }
    }
}
```

#### Opening in VS Code

1. Run `cd ..` to return to the root directory of your project.
2. If you have VS Code command line tools installed, you may navigate to your root project diretory and run `code .`, which will open the working directory in VS Code. If you do not have VS Code command line tools installed, you may open the directory through the VS Code user-interface.
3. VS Code should prompt you to open the Docker container associated with the file inside the `.devcontainer` directory. Follow the instructions to open the Docker container.

#### Create Rust File

1. Create the rust file by running the command `touch main.rs`.
2. Open the newly created file in VS Code and paste in the following code:
```rust
fn main() {
    println!("Hello COMP423");
}
```

#### Compile and run

1. Compile your new rust file with the following command `rustc main.rs`.
2. Run your compiled rust file with the following command `./main`.
3. You should now see the standard output: `Hello COMP423`.