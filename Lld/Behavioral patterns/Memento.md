1) Used to take snapshots of an object
2) To implement this, declare A public static inner class that other objects can use to store the state of the target class
3) inner class will have private constructor
4) will have methods to accept state from target class object, and restore state to the target class object. 
Example

`public class TextArea {
    private String content;

    public void setContent(String content) { this.content = content; }
    public String getContent() { return content; }

    // The Memento is now an inner class
    public static class EditorState {
        private final String content;

        private EditorState(String content) {
            this.content = content;
        }

        // Only accessible to TextArea or through specific logic
        private String getContent() { return content; }
    }

    public EditorState save() {
        return new EditorState(content);
    }

    public void restore(EditorState state) {
        if (state != null) {
            this.content = state.getContent();
        }
    }
}
`