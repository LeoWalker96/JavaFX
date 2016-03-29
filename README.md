# JavaFX
import javax.swing.JOptionPane;
import javafx.application.Application;
import javafx.event.ActionEvent;
import javafx.event.EventHandler;
import javafx.geometry.Insets;
import javafx.geometry.Pos;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.Label;
import javafx.scene.control.PasswordField;
import javafx.scene.control.TextField;
import javafx.scene.layout.GridPane;
import javafx.scene.layout.HBox;
import javafx.scene.text.Font;
import javafx.scene.text.FontWeight;
import javafx.scene.text.Text;
import javafx.stage.Stage;

public class Authentication extends Application {
    public enum AccountType {Administrator, Student, Staff, Guest}
    public void start(Stage primaryStage) {
       String correctUserName = "Leo Walker";
       String correctPassword = "password";
       
       primaryStage.setTitle("JavaFx Welcome");
       GridPane grid = new GridPane();
       grid.setAlignment(Pos.CENTER);
       grid.setHgap(10);
       grid.setVgap(10);
       grid.setPadding(new Insets(25, 25, 25, 25));
       
       Text scenetitle =  new Text("Welcome");
       scenetitle.setFont(Font.font("Tahoma", FontWeight.NORMAL, 20));
       grid.add(scenetitle, 0, 0, 2, 1);

       Label UserName = new Label("User Name:");
       grid.add(UserName, 0, 1);

       TextField UserNameTextField = new TextField();
       grid.add(UserNameTextField, 1, 1);
 
       Label Pw = new Label("Password");
       grid.add(Pw, 0, 2);

       PasswordField PwBox = new PasswordField();
       grid.add(PwBox, 1, 2);

       Button Btn = new Button("Sign In");
       HBox HBBtn = new HBox(10);
       HBBtn.setAlignment(Pos.BOTTOM_RIGHT);
       HBBtn.getChildren().add(Btn);
       grid.add(HBBtn, 1, 4);
      
       Btn.setOnAction(new EventHandler<ActionEvent>() {
            String inputUserName = "Leo Walker";
            String inputPassword = "Password";
            @Override
            public void handle(ActionEvent e) {
               if (correctUserName.equals(inputUserName) && correctPassword.equals(inputPassword)) {
                    AccountType[] choices = {AccountType.Administrator, AccountType.Student, AccountType.Staff, AccountType.Guest};
                    AccountType select = (AccountType) JOptionPane.showInputDialog(null, "Select your account", "Account Type", JOptionPane.INFORMATION_MESSAGE, null, choices, choices[0]);
                    while (select!=null) {
                        switch (select) {
                        case Administrator: JOptionPane.showMessageDialog(null, "Welcome Administrator");break;
                        case Student: JOptionPane.showMessageDialog(null, "Welcome Student");break;
                        case Staff: JOptionPane.showMessageDialog(null, "Welcome Staff");break;
                        case Guest: JOptionPane.showMessageDialog(null, "Welcome Guest");break;
               }
          } select = (AccountType) JOptionPane.showInputDialog(null, "Select your account", "Account Type", JOptionPane.INFORMATION_MESSAGE, null, choices, choices[0]);
          } else {
                  JOptionPane.showMessageDialog(null, "Failed Authentication");
               }
          }
         });
        
             Scene scene = new Scene(grid, 300, 275);
             primaryStage.setScene(scene);
             primaryStage.show();
        }
}     
       
