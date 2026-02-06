🚀 PyAll: Hybrid Language Orchestrator

PyAll is a high-performance bridge that allows you to write and execute C++ and Java code directly inside your Python environment. Powered by a Rust-based process marshall, it eliminates the complexity of manual compilation by automating the build-and-run cycle.

✨ Features

Mixed-Mode Coding: Use the @pyall.cpp decorator to embed C++ blocks inside Python functions.

Direct Execution: Run C++ or Java strings instantly with pyall.run_cpp() or pyall.run_code().

Auto-Fix Engine: Automatically injects missing headers (like <iostream>) and fixes common syntax mistakes in C++ snippets.

Ultra-Fast Core: Compilation orchestration is handled by a native Rust binary for minimal overhead.

Virtual Run: Executes code in isolated temporary directories to keep your filesystem clean.

🛠️ Quick Start

Installation

If you have received the .whl file, simply install it using pip:

pip install pyall-0.1.0-py3-none-any.whl


Prerequisites:

C++ Compiler: g++ (MinGW or GCC) must be installed and added to your system PATH.

📖 Usage

Inside Python (Hybrid Mode)

You can mix Python logic with C++ performance in the same file. The @pyall.cpp decorator reads the C++ code from the function's docstring.

import pyall

@pyall.cpp
def heavy_math():
    """
    int main() {
        std::cout << "Calculating in C++..." << std::endl;
        int sum = 0;
        for(int i=0; i<1000; i++) sum += i;
        std::cout << "Sum: " << sum;
        return 0;
    }
    """

print("Starting Python...")
heavy_math()


Direct String Execution

Perfect for quick snippets or dynamic code generation.

import pyall

result = pyall.run_cpp('int main() { std::cout << "Direct Run Success"; }')
print(result) 


Terminal CLI

PyAll also works as a command-line tool to run source files without manual compiling:

# Run a C++ file
pyall run script.cpp

# Run inline code directly
pyall inline cpp "int main() { std::cout << 'Hello World'; }"


📜 License

MIT
