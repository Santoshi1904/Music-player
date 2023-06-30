# Music-player
import subprocess

# Function to play music using the default media player
def play_music(file):
    try:
        subprocess.run(["xdg-open", file])  # Linux
    except FileNotFoundError:
        try:
            subprocess.run(["open", file])  # macOS
        except FileNotFoundError:
            try:
                subprocess.run(["start", "", file], shell=True)  # Windows
            except FileNotFoundError:
                print("Unable to play music. Please check your operating system support.")

# Function to pause music using the default media player
def pause_music():
    try:
        subprocess.run(["xdotool", "key", "XF86AudioPause"])  # Linux
    except FileNotFoundError:
        try:
            subprocess.run(["osascript", "-e", "tell application \"Music\" to pause"])  # macOS (iTunes)
        except FileNotFoundError:
            try:
                subprocess.run(["nircmd", "sendkey", "ctrl" ,"shift", "P"])  # Windows (Winamp)
            except FileNotFoundError:
                print("Unable to pause music. Please check your operating system support.")

# Function to resume music using the default media player
def resume_music():
    try:
        subprocess.run(["xdotool", "key", "XF86AudioPlay"])  # Linux
    except FileNotFoundError:
        try:
            subprocess.run(["osascript", "-e", "tell application \"Music\" to play"])  # macOS (iTunes)
        except FileNotFoundError:
            try:
                subprocess.run(["nircmd", "sendkey", "ctrl" ,"shift", "P"])  # Windows (Winamp)
            except FileNotFoundError:
                print("Unable to resume music. Please check your operating system support.")

# Function to stop music using the default media player
def stop_music():
    try:
        subprocess.run(["xdotool", "key", "XF86AudioStop"])  # Linux
    except FileNotFoundError:
        try:
            subprocess.run(["osascript", "-e", "tell application \"Music\" to stop"])  # macOS (iTunes)
        except FileNotFoundError:
            try:
                subprocess.run(["nircmd", "sendkey", "ctrl" ,"shift", "S"])  # Windows (Winamp)
            except FileNotFoundError:
                print("Unable to stop music. Please check your operating system support.")

# Take music file path input from the user
music_file = input("Enter the music file path: ")

# Play the music
play_music(music_file)
