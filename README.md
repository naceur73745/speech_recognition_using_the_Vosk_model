# speech_recognition_using_the_Vosk_model
The project starts by importing necessary libraries and modules such as ipywidgets for creating interactive widgets, Queue for managing message and recording queues, Thread for handling concurrent execution, and display for showing output.

Next, two buttons are created using the widgets.Button class: button_for_recording for recording audio and button_to_stop for stopping the recording.

A widget named output is also created using widgets.Output to display the output messages.

After creating the buttons and the output widget, the functions for starting and stopping the recording are defined.

The start_recording function puts a True value into the messages queue and starts two threads: record_microphone for recording the audio and speech_recognition for performing speech recognition on the recorded audio. The output of the speech recognition process is then displayed using the output widget.

The stop_recording function retrieves a message from the messages queue, indicating that the recording should be stopped, and displays a "Stopped." message using the output widget.

The record_button and stop_button buttons are assigned the on_click event handlers to trigger the start_recording and stop_recording functions, respectively.

Finally, the record_button, stop_button, and output widget are displayed using the display function.

Moving on, the project installs the pyaudio library and retrieves the audio device index for the microphone by iterating over the available devices using p.get_device_info_by_index(i).

The project defines the record_microphone function, responsible for recording audio from the microphone. It initializes the PyAudio library, opens a stream with the specified audio format, channels, sample rate, and input device index, and starts recording audio in chunks. The recorded frames are stored in a list, and when the desired duration is reached, the frames are put into the recordings queue. The process continues until the messages queue is empty. Once finished, the stream is stopped, closed, and PyAudio is terminated.

The project also defines the speech_recognition function, which handles the speech recognition process. It retrieves frames from the recordings queue, passes them to the Vosk speech recognition model for recognition, and extracts the recognized text. The recognized text is then processed using an external script called recasepunc.py to recase and punctuate the text. The processed text is appended to the output widget using output.append_stdout. The process continues until the messages queue is empty, with a 1-second delay between iterations.

Overall, this project allows real-time speech recognition by recording audio from a microphone, performing speech recognition using the Vosk model, and displaying the recognized text with recased and punctuated output.
