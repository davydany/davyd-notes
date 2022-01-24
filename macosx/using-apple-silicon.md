# Using Apple Silicon

I recently got a 16" Macbook Pro with the M1 Mac Pro. The following are my continuous reviews,
and things that I had to do to overcome issues I encountered with this laptop:

## Using Homebrew with Apple Silicon

Apple created **Rosetta Stone** to have apps that have not been compiled for the Apple Silicon
to still continue to work. They do this behind the scenes automagically with **Rosetta Stone**.
**Rosetta Stone** is an Intel x64_86 emulator that works behind the scenes.

The problem is with CLI applications, especially with CLI tools installed with Homebrew. To 
overcome this issue, we need to install 2 versions of HomeBrew: one for Intel and one for Apple
Silicon. 

This tutorial shows how to do this: [How to Run Legacy Command Line Apps on Apple Silicon](https://indiespark.top/software/run-command-line-apple-silicon/)