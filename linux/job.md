```
jobs - list the current jobs
fg - resume the job that's next in the queue
fg %[number] - resume job [number]
bg - Push the next job in the queue into the background
bg %[number] - Push the job [number] into the background
kill %[number] - Kill the job numbered [number]
kill -[signal] %[number] - Send the signal [signal] to job number [number]
disown %[number] - disown the process(no more terminal will be owner), so command will be alive even after closing the terminal.
```