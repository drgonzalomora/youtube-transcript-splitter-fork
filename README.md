# GPT-Friendly YouTube Transcript Splitter
---

The **YouTube Transcript Splitter** is a highly efficient tool that streamlines the process of acquiring and processing YouTube video transcripts for use with ChatGPT. This powerful command-line tool empowers you to: (1) retrieve the transcript through the video ID or URL; (2) customize the transcript handling through three distinct processing modes ('separate', 'full', or 'auto'); and (3) conveniently copy the processed transcript to your clipboard, either as a whole or in smaller segments to *accommodate ChatGPT's input limitations*. Moreover, it leverages prompt-engineering techniques to enhance output quality, ensuring a more seamless and user-friendly ChatGPT experience.

**SPANISH:**
El código es un script de Python que utiliza la biblioteca YouTubeTranscriptApi para extraer y procesar transcripciones de videos de YouTube. El script tiene la capacidad de dividir la transcripción en partes más pequeñas y copiarlas en el portapapeles del sistema operativo para su posterior uso.

El script utiliza argumentos de línea de comando para especificar el modo de funcionamiento y la entrada de video de YouTube. Los modos disponibles son 'separate', 'full' y 'auto'. En el modo 'separate', la transcripción se divide en partes más pequeñas para facilitar su uso. En el modo 'full', la transcripción completa se copia en el portapapeles. En el modo 'auto', el script elige automáticamente el modo más adecuado según el tamaño de la transcripción.

El script utiliza expresiones regulares para extraer el ID del video de la entrada de video proporcionada por el usuario. También define una excepción personalizada, InvalidModeError, que se lanza si el modo especificado no es uno de los tres modos permitidos.

El código también utiliza la biblioteca pyperclip para copiar los fragmentos de texto en el portapapeles del sistema operativo. La cantidad máxima de tokens permitidos por parte se define como 1400.

En general, el script permite a los usuarios procesar y utilizar transcripciones de videos de YouTube de manera más eficiente y efectiva.

## Table of Contents
---

1.  [Functionality](#functionality)
2.  [Installation](#installation)
    *   [Clone the Repository](#clone-the-repository)
    *   [Install Requirements](#install-requirements)
3.  [Usage](#usage)
4.  [Function Overview](#function-overview)
5.  [Mode Explanation](#mode-explanation)

## Functionality
---

The YouTube Transcript Summarizer allows you to:

*   Fetch the transcript of a YouTube video using the video ID or URL
*   Process the transcript using one of three modes: 'separate', 'full', or 'auto'
*   Copy the processed transcript to the clipboard in full or as smaller chunks
*   Utilize prompt-engineering techniques to improve the quality of the output

## Installation
---

### Clone the Repository

To get started, clone the repository from GitHub:

bash

```bash
git clone https://github.com/Christoph-Beckmann/youtube-transcript-summarizer.git
cd youtube-transcript-summarizer
```

### Install Requirements

Next, install the required packages using the `requirements.txt` file:

`pip install -r requirements.txt`

## Usage
---
To use the "YouTube Transcript Splitter" command-line tool, follow these steps:

1. Open a terminal (Command Prompt or PowerShell on Windows, Terminal on macOS or Linux).
2. Navigate to the directory where the main.py file is located using the cd command.
3. Run the tool by entering the following command:

```sh
python3 main.py [mode] [YouTube-Link or Video-ID]
```

Replace [mode] with one of the following options:

- `separate`: Splits the transcript into chunks for easier input into ChatGPT.
- `full`: Retrieves the full transcript without splitting.
- `auto`: Automatically splits the transcript if it exceeds a certain number of tokens.

Replace `[YouTube-Link or Video-ID]` with the URL of the YouTube video or its video ID.

The tool will either copy the full transcript or the separate chunks to your clipboard, depending on the mode you choose. You can then paste the content into the ChatGPT interface to utilize the prompt-engineering techniques for summarization.

## Function Overview
---

Here is an overview of each function in the program:

*   `get_video_ID(entry: str) -> str`: Extracts and returns the YouTube video ID from the given input string (either URL or video ID). Returns None if the input is invalid.
*   `get_transcript(video_id: str) -> str`: Fetches and returns the transcript of a YouTube video with the given video ID. Returns an empty string if the transcript is not found.
*   `create_chunks(text: str, max_tokens_per_part: int, mode: str)`: Splits the given text into chunks based on the specified mode and the maximum tokens per part. Returns a list of chunks.
*   `process_args(args) -> tuple`: Processes the command-line arguments and returns a tuple containing the mode and input string. Raises an `InvalidModeError` if the specified mode is not one of 'separate', 'full', or 'auto'.
*   `process_transcript(mode: str, transcript: str) -> list`: Processes the transcript based on the specified mode. If the mode is 'full', the transcript is copied to the clipboard. If the mode is 'separate' or 'auto', the transcript is split into chunks and a list of chunks is returned.
*   `copy_chunks_to_clipboard(chunks: list)`: Copies the chunks of text to the clipboard one at a time, prompting the user to press Enter to copy the next chunk or 'q' to quit.

After following the installation instructions, you can use the YouTube Transcript Summarizer to fetch and process transcripts of your desired YouTube videos.

## Mode Explanation
---

The available modes for processing the transcript are:

*   `separate`: The transcript is split into smaller chunks, with each chunk containing a maximum number of tokens specified by `MAX_TOKENS_PER_PART`. This mode is useful for inputting long transcripts into ChatGPT.
*   `full`: The entire transcript is copied to the clipboard without splitting into smaller chunks.
*   `auto`: The tool automatically determines whether to split the transcript into chunks or copy it in full based on the total number of tokens in the transcript. If the transcript has fewer tokens than `MAX_TOKENS_PER_PART`,
