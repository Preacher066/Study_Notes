Encapsulate a request as an object so you can **parameterize, queue, or undo operations**.
## One-line intuition
Turn requests into objects so the caller doesn’t need to know _how_ the action is done.

Think of Command Pattern in modern systems as:

👉 **"Anything you can queue, retry, or execute later is a command."**

Where is Command Pattern used in Spring?

- `@Transactional` → command with undo (rollback)
    
- `Runnable` / `ExecutorService` → direct command usage
    
- Spring Events → commands as events

Code example

```import java.util.Stack;

// Command interface
interface Command {
    void execute();
    void undo();
}

// Receiver
class Light {
    void on() {
        System.out.println("Light ON");
    }

    void off() {
        System.out.println("Light OFF");
    }
}

// Concrete Command: ON
class LightOnCommand implements Command {
    private Light light;

    LightOnCommand(Light light) {
        this.light = light;
    }

    public void execute() {
        light.on();
    }

    public void undo() {
        light.off();
    }
}

// Concrete Command: OFF
class LightOffCommand implements Command {
    private Light light;

    LightOffCommand(Light light) {
        this.light = light;
    }

    public void execute() {
        light.off();
    }

    public void undo() {
        light.on();
    }
}

// Invoker with history
class RemoteControl {
    private Stack<Command> undoStack = new Stack<>();
    private Stack<Command> redoStack = new Stack<>();

    void executeCommand(Command command) {
        command.execute();
        undoStack.push(command);
        redoStack.clear(); // reset redo on new action
    }

    void undo() {
        if (!undoStack.isEmpty()) {
            Command command = undoStack.pop();
            command.undo();
            redoStack.push(command);
        }
    }

    void redo() {
        if (!redoStack.isEmpty()) {
            Command command = redoStack.pop();
            command.execute();
            undoStack.push(command);
        }
    }
}

// Client
public class Main {
    public static void main(String[] args) {
        Light light = new Light();

        Command on = new LightOnCommand(light);
        Command off = new LightOffCommand(light);

        RemoteControl remote = new RemoteControl();

        remote.executeCommand(on);   // ON
        remote.executeCommand(off);  // OFF

        remote.undo(); // ON
        remote.undo(); // OFF

        remote.redo(); // ON
    }
}
```