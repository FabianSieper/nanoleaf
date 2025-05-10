# Nanoleaf Taskfile Toolkit

This repository provides a collection of Taskfile tasks to help you discover, authenticate, and control your Nanoleaf Light Panels directly from the command line. With a few simple commands, you can:

- Scan your local network to find your Nanoleaf device’s IP.
- Generate and store an API token for future requests.
- Toggle your panels on or off.
- Adjust brightness interactively.

All saved credentials are managed in a `nanoleaf.json` file at the root of this repo.

## Requirements

- **Taskfile** (v3) – [taskfile.dev](https://taskfile.dev/)
- **nmap** – for network scanning.
- **jq** – for JSON parsing.
- **gum** – for interactive prompts in the terminal.
- **curl** – for HTTP requests.
- **Homebrew** (macOS) or your platform’s package manager to install dependencies.

## Installation

1. Clone this repository:

   ```bash
   git clone https://github.com/yourusername/nanoleaf-taskfile.git
   cd nanoleaf-taskfile
   ```

2. Install the required tools via Homebrew:

```bash
task install
```

   > **Note:** On Linux, replace the `brew install` calls in the `install` task with your distro’s package manager.

## Usage

1. **Pair and store your API token**

    Bring you nanoleaf light panel into pairming mode by pressing the off-button for 5 seconds until the led starts blinking. Afterwards, execute the following command:

   ```bash
   task new-nanoleaf
   ```

   The function retreives a pairing token, saves it in a caching-file within the repository and allows you to reference and control the linked nanoleaf in future commands.

2. **Toggle panels on/off**

    > **Note:** To utilize this command, first create a conection to a nanoleaf by executing task "new-nanoleaf" - sett step #1

   ```bash
   task power-toggle
   ```

   Opens an interactive menu to select a device and action (`on` or `off`).

3. **Adjust brightness**

    > **Note:** To utilize this command, first create a conection to a nanoleaf by executing task "new-nanoleaf" - sett step #1

    ```bash
    task brightness
    ```

   Select a device and enter a brightness value (0–100).

## nanoleaf.json

After pairing, `nanoleaf.json` will contain an array of objects:

```json
[
  { "ip": "192.168.178.95", "token": "YourAuthToken" },
  ...
]
```

You can edit or remove entries manually if needed.

---

Happy lighting! 🚀
