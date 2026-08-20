# Richard Slater

I started writing code on a second-hand ZX Spectrum before I was 10, then moved to Visual Basic on Windows. At college I learned Turbo Pascal and Delphi. At university I worked with Ada and Java. Along the way, I have also used C, PHP, SQL, HTML, CSS, and a few other technologies. Professionally I tend to use Go, Rust, C# and Python.

## What I enjoy

I enjoy working where development, security, and operations meet. I care about using [open source software](https://opensource.org/osd) to build a safer future, where commerce and collaboration can grow. I also enjoy keeping up with cryptography. I am exploring [post-quantum cryptography](https://www.nist.gov/pqc) and how it will affect modern IT systems.

## Send me encrypted files

Please encrypt sensitive files before sending them to me. I publish a GPG public key and an age-compatible SSH public key:

- **GPG:** [`https://github.com/richards-ensono.gpg`](https://github.com/richards-ensono.gpg)
- **age:** [`https://github.com/richards-ensono.keys`](https://github.com/richards-ensono.keys)

> [!IMPORTANT]
> Before you use a public key, check it through a separate trusted method. The GPG key fingerprint is `0DD8 5D5A ECA7 F3C9 3832 0A35 6167 02CC B034 D739`.

### Install the software

| Tool | Windows | macOS | Linux |
| --- | --- | --- | --- |
| GPG | [Gpg4win](https://www.gpg4win.org/download.html) | [GnuPG installation options](https://gnupg.org/download/index.html) | [GnuPG installation options](https://gnupg.org/download/index.html) |
| age | [`winget install FiloSottile.age`](https://github.com/FiloSottile/age#installation) | [`brew install age`](https://github.com/FiloSottile/age#installation) | [age installation instructions](https://github.com/FiloSottile/age#installation) |

### Option 1: Encrypt with GPG

1. Download the public key. Use the command for your shell:

   ```sh
   # curl
   curl -fsSLo richards-ensono.gpg https://github.com/richards-ensono.gpg

   # wget
   wget -qO richards-ensono.gpg https://github.com/richards-ensono.gpg
   ```

   ```powershell
   # PowerShell
   Invoke-WebRequest -Uri https://github.com/richards-ensono.gpg -OutFile richards-ensono.gpg
   ```

2. Check that the fingerprint shown matches the one above, then import the key:

   ```sh
   gpg --show-keys --fingerprint richards-ensono.gpg
   gpg --import richards-ensono.gpg
   ```

3. Encrypt the file. This creates a text file that you can attach:

   ```sh
   gpg --armor --output message.txt.asc --encrypt \
     --recipient 0DD85D5AECA7F3C938320A35616702CCB034D739 \
     message.txt
   ```

4. Send `message.txt.asc`, not the original `message.txt`.

### Option 2: Encrypt with age

1. Download the age public key:

   ```sh
   # curl
   curl -fsSLo richards-ensono.keys https://github.com/richards-ensono.keys

   # wget
   wget -qO richards-ensono.keys https://github.com/richards-ensono.keys
   ```

   ```powershell
   # PowerShell
   Invoke-WebRequest -Uri https://github.com/richards-ensono.keys -OutFile richards-ensono.keys
   ```

2. Encrypt the file with the public key:

   ```sh
   age --recipients-file richards-ensono.keys --output message.txt.age message.txt
   ```

3. Send `message.txt.age`, not the original `message.txt`.

> [!IMPORTANT]
> Never send private keys or sensitive content without encrypting it first.
