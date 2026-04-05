## This is a step by step process of how to get your LLMs running on an Android Phone

This is related to my youtube video
https://youtu.be/DRkHAw58irI


1.	Install Termux from Google Play
2.	Once inside termux, run the following
```bash
pkg update && pkg upgrade
pkg install cmake clang make git
```

3.	Go, to llama cpp github and copy the repo.
```bash
git clone https://github.com/ggerganov/llama.cpp.git
cd llama.cpp
```

4.	Build the system
```bash
mkdir build
cd build
cmake ..
cmake  --build . --config Release
```
5.	Make a Models folder inside Build if not available
```bash
mkdir -p models/3B
```
6.	Go to the desired GGUF huggingface link
(a). https://huggingface.co/bartowski/SmallThinker-3B-Preview-GGUF
(b). Select a particular version’s download link eg. https://huggingface.co/bartowski/SmallThinker-3B-Preview-GGUF/resolve/main/SmallThinker-3B-Preview-Q4_K_M.gguf?download=true

7.	Upload the LLM to models folder
(a). type
```bash
curl -L -o models/3B/small.gguf https://huggingface.co/bartowski/SmallThinker-3B-Preview-GGUF/resolve/main/SmallThinker-3B-Preview-Q4_K_M.gguf?download=true
```
(b). This will download the model into the models/3B directory and rename it to small.gguf. It may take some time.

8.	Serve your LLM model
Type this command: 
```bash
./bin/llama-server –model models/3B/small.gguf
```

9.	Go to localhost:8080 for testing the model:

a. 	Go to a browser and type 127.0.0.1:8080
b. 	Play with your model
