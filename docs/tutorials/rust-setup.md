# Setting up a dev container for Rust

* Primary author: [Daniel Ramsgard](https://github.com/DanielRamsgard)
* Reviewer: [Mani Pourfazli](https://github.com/manip1384)

## Prerequisites

### Prerequisite Tools

1. [**Docker Desktop**](https://www.docker.com/products/docker-desktop/)
2. [**VS Code**](https://code.visualstudio.com/download)
3. [**Git**](https://git-scm.com/downloads)
4. A [**GitHub**](https://github.com/) Account

### Prerequisite Knowledge

1. Basic Knowledge of [**Rust Syntax**](https://www.rust-lang.org/learn)
2. Basic Proficiency of [**Git Commands**](https://git-scm.com/doc)
3. [**Docker**](https://docs.docker.com/desktop/) Mental Model

## Steps

- The reader is expected to run the Bash shell whether they are on MacOS, Linux, or Windows.

### Diretory Setup

1. Run the following command `mkdir <name>` to create a new project directory. Now, enter into that directory by executing `cd <name>`.
2. Create a new public repo on GitHub and copy the repo URL.
3. Run the following commands to initialize an empty Git repo locally:
```bash
git init
git remote add origin <GitHub repo URL>
git fetch origin
git switch -c main
```

### Dev Container Configuration

1. Create a new directory called `.devcontainer` and enter into it with the run the following command `mkdir .devcontainer && cd .devcontainer`.
2. Run the following command to configure the devcontainer setup:
```bash
echo "{\n    \"name\": \"Rust Dev Container\",\n    \"image\": \"mcr.microsoft.com/devcontainers/rust:latest\",\n    \"customizations\": {\n        \"vscode\": {\n            \"settings\": {},\n            \"extensions\": [\n                \"rust-lang.rust-analyzer\"\n            ]\n        }\n    }\n}" > devcontainer.json

```

### Opening in VS Code

1. Run `cd ..` to return to the root directory of your project.
2. If you have VS Code command line tools installed and in your PATH, you may run `code .`, which will open the working directory in VS Code. If you do not have VS Code command line tools installed, you may open the directory through the VS Code user-interface.
3. VS Code should prompt you to open the Docker container associated with the file inside the `.devcontainer` directory. Follow the instructions to open the Docker container.

### Compile and run

1. Check the Rust version with the following command `rustc --version`.
2. Create a new binary Rust project without new source control management files by executing the following command `cargo new my_project --vcs none`.
3. Overwrite `my_project/src/main.rs` with the following code:
```rust
fn main() {
    println!("Hello COMP423");
}
```
4. Enter the project and compile the main file with the following command `cd my_project && cargo build`.
5. Run the main.rs file with the following command `cargo run`.
6. You should now see the standard output: `Hello COMP423`.

### Comparison to GCC

`cargo build` is to Rust what `gcc -o my_program my_program.c` is to C. The build command creates an executable object file at the file path: `./target/debug/my_project`. Instead of executing the compiled Rust program with `cargo run`, you may also do `./target/debug/my_project`, similar to running a C program after compiling with GCC: `./my_program`.

### Push to GitHub
- Now execute the following commands to save your changes on GitHub:
```bash
cd ..
echo "Rust hello-world program tutorial link: \`https://danielramsgard.github.io/comp423-course-notes/tutorials/rust-setup\`." > README.md
git add .
git commit -m "my first commit. add README.md and Rust files"
git push origin main
```