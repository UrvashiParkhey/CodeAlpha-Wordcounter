# CodeAlpha-Wordcounter
import javax.swing.*;
import java.awt.event.*;

public class WordCounterApp extends JFrame {
    private JTextArea textArea;
    private JButton countButton;

    public WordCounterApp() {
        setTitle("Word Counter");
        setSize(400, 300);
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        setLayout(null);

        textArea = new JTextArea();
        JScrollPane scrollPane = new JScrollPane(textArea);
        scrollPane.setBounds(20, 20, 350, 200);
        add(scrollPane);

        countButton = new JButton("Count Words");
        countButton.setBounds(20, 230, 150, 30);
        countButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String text = textArea.getText();
                int wordCount = countWords(text);
                JOptionPane.showMessageDialog(WordCounterApp.this, "Word count: " + wordCount);
            }
        });
        add(countButton);

        setVisible(true);
    }

    private int countWords(String text) {
        if (text == null || text.isEmpty()) {
            return 0;
        }
        String[] words = text.split("\\s+");
        return words.length;
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(new Runnable() {
            @Override
            public void run() {
                new WordCounterApp();
            }
        });
    }
}
