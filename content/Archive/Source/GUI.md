## Was ist eine GUI?  
Eine GUI (Graphical User Interface) ist eine grafische Benutzeroberfläche, mit der Anwender über Elemente wie Fenster, Buttons und Menüs mit einer Software interagieren können.  

## Swing  
Swing ist ein plattformunabhängiges GUI-Toolkit für Java, das seit Version 1.2 Teil der Java Foundation Classes (JFC) ist. Es bietet erweiterbare Komponenten und flexible Layouts.

## Hauptfenster JFrame
Ein JFrame ist das Hauptfenster in Swing und dient als Container für alle GUI-Elemente.

```java
import javax.swing.*;

public class MainApp {
   public static void main(String[] args) {
       JFrame frame = new JFrame("Titel");
       frame.setSize(800, 600);                  // Größe (Breite, Höhe)
       frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); // Beenden bei Schließen
       frame.setLocationRelativeTo(null);        // Zentrieren
       frame.setVisible(true);                   // Sichtbar machen
       frame.setResizable(false);                // Größenänderung deaktivieren
       frame.setIconImage(new ImageIcon("icon.png").getImage()); // Icon setzen
   }
}
```

## Inhaltspanel JPanel
Ein JPanel dient als Inhaltspanel in Swing, gruppiert GUI-Komponenten.

```java
JPanel panel = new JPanel();
panel.setLayout(new BorderLayout());
frame.add(panel); // Panel zum JFrame hinzufügen
```

## Schaltflächen JButton

```java
public static void main(String[] args) {
   JButton button = new JButton("Klick mich");
   button.setText("Neuer Text");              // Text ändern
   button.setEnabled(false);                  // Deaktivieren
   button.setToolTipText("Tooltip");         // Tooltip hinzufügen
   button.setIcon(new ImageIcon("icon.png")); // Icon setzen
   button.addActionListener(e -> {            // Klick-Event
       System.out.println("Button geklickt!");
   });
}
```

## Textfelder

### JTextField
Für einzeilige Texteingabe.

```java
public static void main(String[] args) {
   JTextField textField = new JTextField(20); // Einzeilig (20 Zeichen breit)
   textField.setText("Standardtext");         // Text setzen
   String input = textField.getText();        // Text auslesen
}
```

### JTextArea
Für mehrzeilige Texteingabe.

```java
public static void main(String[] args) {
   JTextArea textArea = new JTextArea(5, 20); // 5 Zeilen, 20 Spalten
   textArea.setText("Mehrzeiliger Text\nZeile 2");
   JScrollPane scrollPane = new JScrollPane(textArea); // Scrollbar machen
}
```

## Layout-Manager

### BorderLayout
Teilt den Container in fünf Bereiche.

```java
JFrame frame = new JFrame("BorderLayout Beispiel");
frame.setLayout(new BorderLayout());
frame.add(new JButton("Norden"), BorderLayout.NORTH);
frame.add(new JButton("Zentrum"), BorderLayout.CENTER);
```

### GridLayout
Gleichmäßige Verteilung in Zeilen/Spalten.

```java
frame.setLayout(new GridLayout(2, 3)); // 2 Zeilen, 3 Spalten
for (int i = 1; i <= 6; i++) {
    frame.add(new JButton("Button " + i));
}
```

### BoxLayout
Horizontale oder vertikale Anordnung.

```java
panel.setLayout(new BoxLayout(panel, BoxLayout.Y_AXIS)); // Vertikal
panel.add(new JButton("Button 1"));
```

### FlowLayout
Reihenfolge-Anordnung mit Zeilenumbruch.

```java
frame.setLayout(new FlowLayout());
frame.add(new JButton("Button 1"));
```

## Listen und Dropdowns

### JList

```java
String[] items = {"Item 1", "Item 2"};
JList<String> list = new JList<>(items);
list.setSelectionMode(ListSelectionModel.SINGLE_SELECTION);
```

### JComboBox

```java
JComboBox<String> comboBox = new JComboBox<>(items);
String selected = (String) comboBox.getSelectedItem();
```

## Tabellen JTable

```java
String[] columns = {"Name", "Alter"};
Object[][] data = {{"Max", 25}, {"Anna", 30}};
JTable table = new JTable(data, columns);
JScrollPane scrollPane = new JScrollPane(table);
```

## Event-Handling

### ActionListener (Buttons)

```java
button.addActionListener(e -> {
    System.out.println("Button geklickt!");
});
```

### KeyListener (Tastatur)

```java
textField.addKeyListener(new KeyAdapter(){
    @Override
    public void keyPressed(KeyEvent e) {
        if (e.getKeyCode() == KeyEvent.VK_ENTER) {
            System.out.println("Enter gedrückt!");
        }
    }
});
```

### MouseListener (Maus)

```java
panel.addMouseListener(new MouseAdapter() {
    @Override
    public void mouseClicked(MouseEvent e) {
        System.out.println("Klick bei ("+e.getX()+", "+e.getY()+")");
    }
});
```