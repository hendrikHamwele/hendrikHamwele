import javafx.application.Application;
import javafx.geometry.Insets;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.Label;
import javafx.scene.control.TextField;
import javafx.scene.layout.GridPane;
import javafx.stage.Stage;

public class DataCapturingApplication extends Application {

    private TextField nameField = new TextField();
    private TextField ageField = new TextField();
    private TextField emailField = new TextField();
    private Label resultLabel = new Label();

    public static void main(String[] args) {
        launch(args);
    }

    @Override
    public void start(Stage primaryStage) {
        primaryStage.setTitle("Data Capturing Application");

        GridPane grid = new GridPane();
        grid.setPadding(new Insets(10, 10, 10, 10));
        grid.setVgap(5);
        grid.setHgap(5);

        // Add UI components
        grid.add(new Label("Name:"), 0, 0);
        grid.add(nameField, 1, 0);
        grid.add(new Label("Age:"), 0, 1);
        grid.add(ageField, 1, 1);
        grid.add(new Label("Email:"), 0, 2);
        grid.add(emailField, 1, 2);

        Button captureButton = new Button("Capture");
        captureButton.setOnAction(e -> captureData());
        grid.add(captureButton, 1, 3);

        grid.add(resultLabel, 0, 4, 2, 1);

        Scene scene = new Scene(grid, 300, 200);
        primaryStage.setScene(scene);

        primaryStage.show();
    }

    private void captureData() {
        String name = nameField.getText();
        String ageText = ageField.getText();
        String email = emailField.getText();

        try {
            int age = Integer.parseInt(ageText);

            // Display captured data
            resultLabel.setText("Captured Information:\nName: " + name + "\nAge: " + age + "\nEmail: " + email);
        } catch (NumberFormatException e) {
            resultLabel.setText("Invalid age. Please enter a valid number.");
        }
    }
}

