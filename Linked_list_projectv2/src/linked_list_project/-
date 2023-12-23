/*

 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/GUIForms/JFrame.java to edit this template
 */
package linked_list_project;


import java.io.BufferedReader;
import java.io.File;
import javax.swing.table.DefaultTableModel;
import java.io.FileReader;
import java.util.List;
import java.lang.Object;
import java.io.FileNotFoundException;
import java.io.FileWriter;
import java.io.IOException;
//import com.opencsv;

import java.io.Reader;
import java.nio.file.Files;
import java.nio.file.Paths;
import java.util.ArrayList;
import java.util.Arrays;
import javax.swing.JFileChooser;




public class Linked_list_UI extends javax.swing.JFrame {

    public class Node{
    String data;
    Node prev;
    Node next;
        public Node(String data){
             this.data=data;
             this.prev=null;
             this.next=null;
        }
    }
    public class DoublyLinkedList{
        Node first;
        Node last;
        public DoublyLinkedList(){
        this.first=null;
        this.last=null;
            }
        // Traversing from first to the end of the list 
        public void traverseForward() { 
	Node current = first; 
	while (current != null) { 
		current = current.next; 
            } 
        } 
        // Traversing from tail to the head 
        public void traverseBackward() { 
	Node current = last; 
	while (current != null) {  
		current = current.prev; 
            } 
        } 
        public void insertAtBeginning(String data) { 
	Node temp = new Node (data); 
	if (first == null) { 
		first = temp; 
		last = temp; 
            } 
	else { 
		temp.next = first; 
		first.prev = temp; 
		first= temp; 
            } 
        
        }
        public void insertAtEnd(String data) { 
	Node temp = new Node(data); 
	if (last == null) { 
		first = temp; 
		last = temp; 
            } 
	else { 
		last.next = temp; 
		temp.prev = last; 
		last = temp; 
            } 
        } 
        public void insertAtPosition(String data, int position) { 
            Node temp = new Node(data); 
            if (position == 1) { 
                insertAtBeginning(data); 
                } 
            else{ 
                Node current = first; 
                int currPosition = 1; 
                while (current != null && currPosition < position) { 
                    current = current.next; 
                    currPosition++; 
                    } 
                if (current == null) { 
                    insertAtEnd(data); 
                    } 
                else { 
                    temp.next = current; 
                    temp.prev = current.prev; 
                    current.prev.next = temp; 
                    current.prev = temp; 
                    } 
                } 
            } 
        public void deleteAtBeginning() { 
            if (first == null) { 
		return; 
            } 

	if (first == last) { 
            first = null; 
            last = null; 
            return; 
            } 

            Node temp = first; 
            first = first.next; 
            first.prev = null; 
            temp.next = null; 
        }
        public void deleteAtEnd() { 
            if (last == null) { 
		return; 
            } 

            if (first == last) { 
		first = null; 
		last = null; 
		return; 
            } 

            Node temp = last; 
            last = last.prev; 
            last.next = null; 
            temp.prev = null; 
        }
        public void delete(int pos) { 
            if (first == null) { 
		return; 
            } 

            if (pos == 1) { 
		deleteAtBeginning(); 
		return; 
            } 

            Node current = first; 
            int count = 1; 

            while (current != null && count != pos) { 
		current = current.next; 
		count++; 
            } 

            if (current == null) { 
		System.out.println("Position wrong"); 
		return; 
            } 

            if (current == last) { 
		deleteAtEnd(); 
		return; 
            } 

            current.prev.next = current.next; 
            current.next.prev = current.prev; 
            current.prev = null; 
            current.next = null; 
        } 
    }
DoublyLinkedList first_name = new DoublyLinkedList();
DoublyLinkedList last_name = new DoublyLinkedList();
DoublyLinkedList city = new DoublyLinkedList();
DoublyLinkedList state= new DoublyLinkedList();
DoublyLinkedList id_num = new DoublyLinkedList();
    public class CSV{
    }
private void updateSelectedRow() {
    DefaultTableModel model = (DefaultTableModel) table.getModel();
    int selectedRow = table.getSelectedRow();

    if (selectedRow != -1) {
        String[] newData = {
            box_first.getText(),
            box_last.getText(),
            box_city.getText(),
            box_state.getText(),
            box_id.getText()
        };

        for (int i = 0; i < newData.length; i++) {
            model.setValueAt(newData[i], selectedRow, i);
        }

        // Optionally, update the linked lists if needed
        // Assuming the linked lists are updated in parallel with the table
        first_name.delete(selectedRow + 1); // Adjust index due to linked list implementation
        last_name.delete(selectedRow + 1);
        city.delete(selectedRow + 1);
        state.delete(selectedRow + 1);
        id_num.delete(selectedRow + 1);

        first_name.insertAtPosition(newData[0], selectedRow + 1);
        last_name.insertAtPosition(newData[1], selectedRow + 1);
        city.insertAtPosition(newData[2], selectedRow + 1);
        state.insertAtPosition(newData[3], selectedRow + 1);
        id_num.insertAtPosition(newData[4], selectedRow + 1);
    } else {
        // Handle no row selected
        System.out.println("Please select a row to update.");
    }
}
// ActionListener for the update button or any event that triggers the update action

// Method to save table data to a CSV file
private void saveTableDataToCSV(String filePath) {
    try (FileWriter writer = new FileWriter(filePath)) {
        DefaultTableModel model = (DefaultTableModel) table.getModel();
        int rowCount = model.getRowCount();
        int columnCount = model.getColumnCount();

        // Write the table data
        for (int row = 0; row < rowCount; row++) {
            for (int col = 0; col < columnCount; col++) {
                writer.append(model.getValueAt(row, col).toString());
                if (col < columnCount - 1) {
                    writer.append(',');
                }
            }
            writer.append('\n'); // Add a line break after writing each row
        }

        System.out.println("Table data saved to " + filePath);
    } catch (IOException e) {
        e.printStackTrace();
    }
}


private void addDataToTable() {
    DefaultTableModel model = (DefaultTableModel) table.getModel();

    // Get data from text fields
    String firstName = box_first.getText();
    String lastName = box_last.getText();
    String city = box_city.getText();
    String state = box_state.getText();
    String id = box_id.getText();

    // Add data to the table as a new row
    model.addRow(new Object[]{firstName, lastName, city, state, id});
}
private void addDataToBeginningOfTable() {
    DefaultTableModel model = (DefaultTableModel) table.getModel();

    // Get data from text fields
    String firstName = box_first.getText();
    String lastName = box_last.getText();
    String city = box_city.getText();
    String state = box_state.getText();
    String id = box_id.getText();

    // Insert data at the beginning of the table
    model.insertRow(0, new Object[]{firstName, lastName, city, state, id});
}
private void deleteSelectedRow() {
    DefaultTableModel model = (DefaultTableModel) table.getModel();
    int selectedRow = table.getSelectedRow();

    if (selectedRow >= 0) {
        model.removeRow(selectedRow);
    } else {
        // If no row is selected, you can prompt the user or handle it as needed
        System.out.println("Please select a row to delete.");
    }
}
// ActionListener for the Save menu item or button
private void saveMenuItemActionPerformed() {
    // Replace "filePath" with the path where you want to save the CSV file
     JFileChooser fileChooser = new JFileChooser();
    int returnValue = fileChooser.showSaveDialog(this);

    if (returnValue == JFileChooser.APPROVE_OPTION) {
        File selectedFile = fileChooser.getSelectedFile();
        String filePath = selectedFile.getAbsolutePath();

        saveTableDataToCSV(filePath);
    }
}



    public Linked_list_UI() {
            initComponents();
            jButton1.setVisible(false);
            jButton5.setVisible(false);
            jButton6.setVisible(false);
              
    }

    /**
     * This method is called from within the constructor to initialize the form.
     * WARNING: Do NOT modify this code. The content of this method is always
     * regenerated by the Form Editor.
     */
    @SuppressWarnings("unchecked")
    // <editor-fold defaultstate="collapsed" desc="Generated Code">//GEN-BEGIN:initComponents
    private void initComponents() {

        File = new javax.swing.JFrame();
        jFileChooser1 = new javax.swing.JFileChooser();
        jPanel1 = new javax.swing.JPanel();
        box_first = new javax.swing.JTextField();
        jLabel1 = new javax.swing.JLabel();
        jLabel4 = new javax.swing.JLabel();
        box_city = new javax.swing.JTextField();
        box_id = new javax.swing.JTextField();
        box_last = new javax.swing.JTextField();
        jLabel3 = new javax.swing.JLabel();
        jLabel2 = new javax.swing.JLabel();
        box_state = new javax.swing.JTextField();
        jLabel5 = new javax.swing.JLabel();
        filler1 = new javax.swing.Box.Filler(new java.awt.Dimension(0, 0), new java.awt.Dimension(0, 0), new java.awt.Dimension(32767, 32767));
        jButton1 = new javax.swing.JButton();
        filler2 = new javax.swing.Box.Filler(new java.awt.Dimension(0, 0), new java.awt.Dimension(0, 0), new java.awt.Dimension(32767, 32767));
        jScrollPane1 = new javax.swing.JScrollPane();
        table = new javax.swing.JTable();
        jButton3 = new javax.swing.JButton();
        jButton4 = new javax.swing.JButton();
        jButton5 = new javax.swing.JButton();
        jButton6 = new javax.swing.JButton();
        filler3 = new javax.swing.Box.Filler(new java.awt.Dimension(0, 0), new java.awt.Dimension(0, 0), new java.awt.Dimension(32767, 32767));
        filler4 = new javax.swing.Box.Filler(new java.awt.Dimension(0, 0), new java.awt.Dimension(0, 0), new java.awt.Dimension(32767, 32767));
        jMenuBar1 = new javax.swing.JMenuBar();
        File_menu = new javax.swing.JMenu();
        Import_button = new javax.swing.JMenuItem();
        Save = new javax.swing.JMenuItem();
        SaveAs = new javax.swing.JMenuItem();
        Edit_menu = new javax.swing.JMenu();

        File.setDefaultCloseOperation(javax.swing.WindowConstants.EXIT_ON_CLOSE);
        File.setAlwaysOnTop(true);
        File.setCursor(new java.awt.Cursor(java.awt.Cursor.DEFAULT_CURSOR));
        File.setResizable(false);
        File.setType(java.awt.Window.Type.POPUP);

        jFileChooser1.setAccessory(Import_button);
        jFileChooser1.setApproveButtonToolTipText("");
        jFileChooser1.setCurrentDirectory(new java.io.File("C:\\Users\\Public"));
        jFileChooser1.setFileSelectionMode(javax.swing.JFileChooser.FILES_AND_DIRECTORIES);
        jFileChooser1.setInheritsPopupMenu(true);
        jFileChooser1.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                jFileChooser1ActionPerformed(evt);
            }
        });

        javax.swing.GroupLayout FileLayout = new javax.swing.GroupLayout(File.getContentPane());
        File.getContentPane().setLayout(FileLayout);
        FileLayout.setHorizontalGroup(
            FileLayout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(javax.swing.GroupLayout.Alignment.TRAILING, FileLayout.createSequentialGroup()
                .addContainerGap(15, Short.MAX_VALUE)
                .addComponent(jFileChooser1, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE)
                .addContainerGap())
        );
        FileLayout.setVerticalGroup(
            FileLayout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(javax.swing.GroupLayout.Alignment.TRAILING, FileLayout.createSequentialGroup()
                .addContainerGap(javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE)
                .addComponent(jFileChooser1, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE)
                .addContainerGap())
        );

        setDefaultCloseOperation(javax.swing.WindowConstants.EXIT_ON_CLOSE);

        box_first.setHorizontalAlignment(javax.swing.JTextField.CENTER);
        box_first.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                box_firstActionPerformed(evt);
            }
        });

        jLabel1.setHorizontalAlignment(javax.swing.SwingConstants.CENTER);
        jLabel1.setText("First Name");
        jLabel1.setHorizontalTextPosition(javax.swing.SwingConstants.CENTER);

        jLabel4.setHorizontalAlignment(javax.swing.SwingConstants.CENTER);
        jLabel4.setText("Embloyee ID");
        jLabel4.setHorizontalTextPosition(javax.swing.SwingConstants.CENTER);

        box_city.setHorizontalAlignment(javax.swing.JTextField.CENTER);
        box_city.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                box_cityActionPerformed(evt);
            }
        });

        box_id.setHorizontalAlignment(javax.swing.JTextField.CENTER);

        box_last.setHorizontalAlignment(javax.swing.JTextField.CENTER);
        box_last.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                box_lastActionPerformed(evt);
            }
        });

        jLabel3.setHorizontalAlignment(javax.swing.SwingConstants.CENTER);
        jLabel3.setText("City");
        jLabel3.setHorizontalTextPosition(javax.swing.SwingConstants.CENTER);

        jLabel2.setHorizontalAlignment(javax.swing.SwingConstants.CENTER);
        jLabel2.setText("Last Name");
        jLabel2.setHorizontalTextPosition(javax.swing.SwingConstants.CENTER);

        box_state.setHorizontalAlignment(javax.swing.JTextField.CENTER);
        box_state.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                box_stateActionPerformed(evt);
            }
        });

        jLabel5.setHorizontalAlignment(javax.swing.SwingConstants.CENTER);
        jLabel5.setText("State");
        jLabel5.setHorizontalTextPosition(javax.swing.SwingConstants.CENTER);

        javax.swing.GroupLayout jPanel1Layout = new javax.swing.GroupLayout(jPanel1);
        jPanel1.setLayout(jPanel1Layout);
        jPanel1Layout.setHorizontalGroup(
            jPanel1Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(jPanel1Layout.createSequentialGroup()
                .addContainerGap()
                .addGroup(jPanel1Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                    .addComponent(box_first)
                    .addComponent(jLabel1, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE))
                .addPreferredGap(javax.swing.LayoutStyle.ComponentPlacement.RELATED)
                .addGroup(jPanel1Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                    .addComponent(box_last)
                    .addComponent(jLabel2, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE))
                .addPreferredGap(javax.swing.LayoutStyle.ComponentPlacement.RELATED)
                .addGroup(jPanel1Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                    .addComponent(box_city)
                    .addComponent(jLabel3, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE))
                .addPreferredGap(javax.swing.LayoutStyle.ComponentPlacement.RELATED)
                .addGroup(jPanel1Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                    .addComponent(box_state)
                    .addComponent(jLabel5, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE))
                .addPreferredGap(javax.swing.LayoutStyle.ComponentPlacement.RELATED)
                .addGroup(jPanel1Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                    .addComponent(jLabel4, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE)
                    .addComponent(box_id))
                .addContainerGap())
        );
        jPanel1Layout.setVerticalGroup(
            jPanel1Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(jPanel1Layout.createSequentialGroup()
                .addContainerGap()
                .addGroup(jPanel1Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                    .addComponent(jLabel5, javax.swing.GroupLayout.Alignment.TRAILING, javax.swing.GroupLayout.PREFERRED_SIZE, 31, javax.swing.GroupLayout.PREFERRED_SIZE)
                    .addComponent(jLabel3, javax.swing.GroupLayout.PREFERRED_SIZE, 31, javax.swing.GroupLayout.PREFERRED_SIZE)
                    .addComponent(jLabel2, javax.swing.GroupLayout.Alignment.TRAILING, javax.swing.GroupLayout.PREFERRED_SIZE, 31, javax.swing.GroupLayout.PREFERRED_SIZE)
                    .addComponent(jLabel1, javax.swing.GroupLayout.PREFERRED_SIZE, 31, javax.swing.GroupLayout.PREFERRED_SIZE)
                    .addComponent(jLabel4, javax.swing.GroupLayout.PREFERRED_SIZE, 31, javax.swing.GroupLayout.PREFERRED_SIZE))
                .addPreferredGap(javax.swing.LayoutStyle.ComponentPlacement.RELATED)
                .addGroup(jPanel1Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                    .addComponent(box_last, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE)
                    .addComponent(box_id, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE)
                    .addComponent(box_first, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE)
                    .addComponent(box_city, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE)
                    .addComponent(box_state, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE))
                .addGap(8, 8, 8))
        );

        jButton1.setText("Confirm Change");
        jButton1.setBorder(new javax.swing.border.SoftBevelBorder(javax.swing.border.BevelBorder.RAISED));
        jButton1.setHorizontalTextPosition(javax.swing.SwingConstants.CENTER);
        jButton1.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                jButton1ActionPerformed(evt);
            }
        });

        table.setModel(new javax.swing.table.DefaultTableModel(
            new Object [][] {

            },
            new String [] {
                "First Name", "Last Name", "City", "State", "Employee ID"
            }
        ) {
            Class[] types = new Class [] {
                java.lang.String.class, java.lang.String.class, java.lang.String.class, java.lang.String.class, java.lang.String.class
            };
            boolean[] canEdit = new boolean [] {
                false, false, false, false, false
            };

            public Class getColumnClass(int columnIndex) {
                return types [columnIndex];
            }

            public boolean isCellEditable(int rowIndex, int columnIndex) {
                return canEdit [columnIndex];
            }
        });
        table.setAutoResizeMode(javax.swing.JTable.AUTO_RESIZE_ALL_COLUMNS);
        table.setCursor(new java.awt.Cursor(java.awt.Cursor.DEFAULT_CURSOR));
        table.getTableHeader().setReorderingAllowed(false);
        table.addMouseListener(new java.awt.event.MouseAdapter() {
            public void mouseClicked(java.awt.event.MouseEvent evt) {
                tableMouseClicked(evt);
            }
            public void mouseEntered(java.awt.event.MouseEvent evt) {
                tableMouseEntered(evt);
            }
            public void mouseExited(java.awt.event.MouseEvent evt) {
                tableMouseExited(evt);
            }
        });
        table.addKeyListener(new java.awt.event.KeyAdapter() {
            public void keyPressed(java.awt.event.KeyEvent evt) {
                tableKeyPressed(evt);
            }
            public void keyTyped(java.awt.event.KeyEvent evt) {
                tableKeyTyped(evt);
                ConfirmKeyTyped(evt);
            }
        });
        jScrollPane1.setViewportView(table);

        jButton3.setText("Add Beginning");
        jButton3.setBorder(new javax.swing.border.SoftBevelBorder(javax.swing.border.BevelBorder.RAISED));
        jButton3.setHorizontalTextPosition(javax.swing.SwingConstants.CENTER);
        jButton3.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                jButton3ActionPerformed(evt);
            }
        });

        jButton4.setText("Add End");
        jButton4.setBorder(new javax.swing.border.SoftBevelBorder(javax.swing.border.BevelBorder.RAISED));
        jButton4.setHorizontalTextPosition(javax.swing.SwingConstants.CENTER);
        jButton4.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                jButton4ActionPerformed(evt);
            }
        });

        jButton5.setText("Delete");
        jButton5.setBorder(new javax.swing.border.SoftBevelBorder(javax.swing.border.BevelBorder.RAISED));
        jButton5.setHorizontalTextPosition(javax.swing.SwingConstants.CENTER);
        jButton5.setMaximumSize(new java.awt.Dimension(50, 22));
        jButton5.setMinimumSize(new java.awt.Dimension(50, 22));
        jButton5.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                jButton5ActionPerformed(evt);
            }
        });

        jButton6.setText("Unselect");
        jButton6.setBorder(new javax.swing.border.SoftBevelBorder(javax.swing.border.BevelBorder.RAISED));
        jButton6.setHorizontalTextPosition(javax.swing.SwingConstants.CENTER);
        jButton6.setMaximumSize(new java.awt.Dimension(50, 22));
        jButton6.setMinimumSize(new java.awt.Dimension(50, 22));
        jButton6.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                jButton6ActionPerformed(evt);
            }
        });

        jMenuBar1.setBorder(javax.swing.BorderFactory.createBevelBorder(javax.swing.border.BevelBorder.RAISED, new java.awt.Color(204, 204, 204), new java.awt.Color(204, 204, 204), null, null));

        File_menu.setText("File");

        Import_button.setAccelerator(javax.swing.KeyStroke.getKeyStroke(java.awt.event.KeyEvent.VK_I, java.awt.event.InputEvent.CTRL_DOWN_MASK));
        Import_button.setText("Import");
        Import_button.setInheritsPopupMenu(true);
        Import_button.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                Import_buttonActionPerformed(evt);
            }
        });
        File_menu.add(Import_button);

        Save.setAccelerator(javax.swing.KeyStroke.getKeyStroke(java.awt.event.KeyEvent.VK_S, java.awt.event.InputEvent.CTRL_DOWN_MASK));
        Save.setText("Save");
        Save.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                SaveActionPerformed(evt);
            }
        });
        File_menu.add(Save);

        SaveAs.setAccelerator(javax.swing.KeyStroke.getKeyStroke(java.awt.event.KeyEvent.VK_S, java.awt.event.InputEvent.SHIFT_DOWN_MASK | java.awt.event.InputEvent.CTRL_DOWN_MASK));
        SaveAs.setText("Save As");
        File_menu.add(SaveAs);

        jMenuBar1.add(File_menu);

        Edit_menu.setText("Edit");
        jMenuBar1.add(Edit_menu);

        setJMenuBar(jMenuBar1);

        javax.swing.GroupLayout layout = new javax.swing.GroupLayout(getContentPane());
        getContentPane().setLayout(layout);
        layout.setHorizontalGroup(
            layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(layout.createSequentialGroup()
                .addGroup(layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                    .addGroup(layout.createSequentialGroup()
                        .addContainerGap()
                        .addComponent(jScrollPane1, javax.swing.GroupLayout.DEFAULT_SIZE, 660, Short.MAX_VALUE))
                    .addGroup(layout.createSequentialGroup()
                        .addGap(12, 12, 12)
                        .addComponent(jPanel1, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE))
                    .addGroup(layout.createSequentialGroup()
                        .addContainerGap()
                        .addComponent(filler2, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE)
                        .addPreferredGap(javax.swing.LayoutStyle.ComponentPlacement.RELATED)
                        .addGroup(layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                            .addGroup(layout.createParallelGroup(javax.swing.GroupLayout.Alignment.TRAILING)
                                .addGroup(layout.createParallelGroup(javax.swing.GroupLayout.Alignment.TRAILING)
                                    .addGroup(layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                                        .addGroup(layout.createParallelGroup(javax.swing.GroupLayout.Alignment.TRAILING, false)
                                            .addComponent(filler4, javax.swing.GroupLayout.DEFAULT_SIZE, 124, Short.MAX_VALUE)
                                            .addComponent(filler3, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE))
                                        .addComponent(jButton3, javax.swing.GroupLayout.PREFERRED_SIZE, 124, javax.swing.GroupLayout.PREFERRED_SIZE))
                                    .addComponent(jButton4, javax.swing.GroupLayout.PREFERRED_SIZE, 124, javax.swing.GroupLayout.PREFERRED_SIZE))
                                .addComponent(jButton1, javax.swing.GroupLayout.PREFERRED_SIZE, 124, javax.swing.GroupLayout.PREFERRED_SIZE))
                            .addComponent(jButton5, javax.swing.GroupLayout.PREFERRED_SIZE, 124, javax.swing.GroupLayout.PREFERRED_SIZE)
                            .addComponent(jButton6, javax.swing.GroupLayout.PREFERRED_SIZE, 124, javax.swing.GroupLayout.PREFERRED_SIZE))
                        .addPreferredGap(javax.swing.LayoutStyle.ComponentPlacement.RELATED)
                        .addComponent(filler1, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE)))
                .addContainerGap())
        );
        layout.setVerticalGroup(
            layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(layout.createSequentialGroup()
                .addContainerGap()
                .addComponent(jScrollPane1, javax.swing.GroupLayout.DEFAULT_SIZE, 231, Short.MAX_VALUE)
                .addPreferredGap(javax.swing.LayoutStyle.ComponentPlacement.RELATED)
                .addComponent(jPanel1, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE)
                .addPreferredGap(javax.swing.LayoutStyle.ComponentPlacement.RELATED)
                .addGroup(layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                    .addGroup(layout.createSequentialGroup()
                        .addComponent(filler3, javax.swing.GroupLayout.PREFERRED_SIZE, 17, javax.swing.GroupLayout.PREFERRED_SIZE)
                        .addPreferredGap(javax.swing.LayoutStyle.ComponentPlacement.RELATED)
                        .addComponent(jButton3)
                        .addPreferredGap(javax.swing.LayoutStyle.ComponentPlacement.RELATED)
                        .addComponent(jButton4)
                        .addPreferredGap(javax.swing.LayoutStyle.ComponentPlacement.RELATED)
                        .addComponent(jButton1)
                        .addPreferredGap(javax.swing.LayoutStyle.ComponentPlacement.RELATED)
                        .addComponent(jButton5, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE)
                        .addPreferredGap(javax.swing.LayoutStyle.ComponentPlacement.RELATED)
                        .addComponent(jButton6, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE)
                        .addPreferredGap(javax.swing.LayoutStyle.ComponentPlacement.RELATED)
                        .addComponent(filler4, javax.swing.GroupLayout.PREFERRED_SIZE, 14, javax.swing.GroupLayout.PREFERRED_SIZE)
                        .addGap(0, 4, Short.MAX_VALUE))
                    .addComponent(filler1, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE)
                    .addComponent(filler2, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE))
                .addContainerGap())
        );

        pack();
    }// </editor-fold>//GEN-END:initComponents

    private void jButton1ActionPerformed(java.awt.event.ActionEvent evt) {//GEN-FIRST:event_jButton1ActionPerformed
     updateSelectedRow();
    }//GEN-LAST:event_jButton1ActionPerformed

    private void SaveActionPerformed(java.awt.event.ActionEvent evt) {//GEN-FIRST:event_SaveActionPerformed
        // TODO add your handling code here:
        saveMenuItemActionPerformed();
    }//GEN-LAST:event_SaveActionPerformed

    private void tableKeyPressed(java.awt.event.KeyEvent evt) {//GEN-FIRST:event_tableKeyPressed
        // TODO add your handling code here:
    }//GEN-LAST:event_tableKeyPressed

    private void tableMouseEntered(java.awt.event.MouseEvent evt) {//GEN-FIRST:event_tableMouseEntered
        // TODO add your handling code here:
    }//GEN-LAST:event_tableMouseEntered

    private void tableMouseExited(java.awt.event.MouseEvent evt) {//GEN-FIRST:event_tableMouseExited
        // TODO add your handling code here:
    }//GEN-LAST:event_tableMouseExited

    private void tableMouseClicked(java.awt.event.MouseEvent evt) {//GEN-FIRST:event_tableMouseClicked
       int selected_row=table.getSelectedRow();
        int value=0;
        DefaultTableModel model = (DefaultTableModel) table.getModel();
        box_first.setText((String) model.getValueAt(selected_row,value));
        value++;
        box_last.setText((String)model.getValueAt(selected_row, value));
         value++;
        box_city.setText((String)model.getValueAt(selected_row, value));
        value++;
        box_state.setText((String)model.getValueAt(selected_row, value));
        value++;
        box_id.setText((String)model.getValueAt(selected_row,value));
       
        if(table.getSelectedRow()>=0){
          jButton1.setVisible(true);
          jButton5.setVisible(true);
          jButton6.setVisible(true);
          jButton3.setVisible(false);
          jButton4.setVisible(false);
      }
    }//GEN-LAST:event_tableMouseClicked

    private void tableKeyTyped(java.awt.event.KeyEvent evt) {//GEN-FIRST:event_tableKeyTyped
        // TODO add your handling code here:
    }//GEN-LAST:event_tableKeyTyped

    private void ConfirmKeyTyped(java.awt.event.KeyEvent evt) {//GEN-FIRST:event_ConfirmKeyTyped
        // TODO add your handling code here:
    }//GEN-LAST:event_ConfirmKeyTyped

    private void box_stateActionPerformed(java.awt.event.ActionEvent evt) {//GEN-FIRST:event_box_stateActionPerformed

        // TODO add your handling code here:
    }//GEN-LAST:event_box_stateActionPerformed

    private void box_lastActionPerformed(java.awt.event.ActionEvent evt) {//GEN-FIRST:event_box_lastActionPerformed
        // TODO add your handling code here:
    }//GEN-LAST:event_box_lastActionPerformed

    private void box_cityActionPerformed(java.awt.event.ActionEvent evt) {//GEN-FIRST:event_box_cityActionPerformed
        // TODO add your handling code here:
    }//GEN-LAST:event_box_cityActionPerformed

    private void box_firstActionPerformed(java.awt.event.ActionEvent evt) {//GEN-FIRST:event_box_firstActionPerformed

    }//GEN-LAST:event_box_firstActionPerformed

    private void Import_buttonActionPerformed(java.awt.event.ActionEvent evt) {//GEN-FIRST:event_Import_buttonActionPerformed
    // Open a file chooser dialog
    int returnVal = jFileChooser1.showOpenDialog(this);
    if (returnVal == JFileChooser.APPROVE_OPTION) {
        File file = jFileChooser1.getSelectedFile();
        try {
            // Clear existing data
            first_name = new DoublyLinkedList();
            last_name = new DoublyLinkedList();
            city = new DoublyLinkedList();
            state = new DoublyLinkedList();
            id_num = new DoublyLinkedList();
            DefaultTableModel model = (DefaultTableModel) table.getModel();
            model.setRowCount(0); // Clear the table

            // Read and parse the CSV file
            List<List<String>> records = new ArrayList<>();
            try (BufferedReader br = new BufferedReader(new FileReader(file))) {
                String line;
                while ((line = br.readLine()) != null) {
                    String[] values = line.split(",");
                    records.add(Arrays.asList(values));

                    // Assuming the CSV format is: First Name, Last Name, City, State, ID
                    if (values.length >= 5) {
                        first_name.insertAtEnd(values[0]);
                        last_name.insertAtEnd(values[1]);
                        city.insertAtEnd(values[2]);
                        state.insertAtEnd(values[3]);
                        id_num.insertAtEnd(values[4]);

                        // Add row to the table
                        model.addRow(new String[]{values[0], values[1], values[2], values[3], values[4]});
                    }
                }
            }
        } catch (IOException ex) {
            ex.printStackTrace();
            // Handle exceptions or errors here
        }
    }


    }//GEN-LAST:event_Import_buttonActionPerformed

    private void jFileChooser1ActionPerformed(java.awt.event.ActionEvent evt) {//GEN-FIRST:event_jFileChooser1ActionPerformed
        // TODO add your handling code here:
    }//GEN-LAST:event_jFileChooser1ActionPerformed

    private void jButton3ActionPerformed(java.awt.event.ActionEvent evt) {//GEN-FIRST:event_jButton3ActionPerformed
        // TODO add your handling code here:
        addDataToBeginningOfTable();
        
    }//GEN-LAST:event_jButton3ActionPerformed

    private void jButton4ActionPerformed(java.awt.event.ActionEvent evt) {//GEN-FIRST:event_jButton4ActionPerformed
        // TODO add your handling code here:
        addDataToTable();
    }//GEN-LAST:event_jButton4ActionPerformed

    private void jButton5ActionPerformed(java.awt.event.ActionEvent evt) {//GEN-FIRST:event_jButton5ActionPerformed
        // TODO add your handling code here:
        deleteSelectedRow();
    }//GEN-LAST:event_jButton5ActionPerformed

    private void jButton6ActionPerformed(java.awt.event.ActionEvent evt) {//GEN-FIRST:event_jButton6ActionPerformed
        // TODO add your handling code here:
        table.clearSelection();
        jButton6.setVisible(false);
        jButton5.setVisible(false);
        jButton1.setVisible(false);
        jButton3.setVisible(true);
        jButton4.setVisible(true);
        
    }//GEN-LAST:event_jButton6ActionPerformed

    /**
     * @param args the command line arguments
     */
    public static void main(String args[]) {
        
        /* Set the Nimbus look and feel */
        //<editor-fold defaultstate="collapsed" desc=" Look and feel setting code (optional) ">
        /* If Nimbus (introduced in Java SE 6) is not available, stay with the default look and feel.
         * For details see http://download.oracle.com/javase/tutorial/uiswing/lookandfeel/plaf.html 
         */
        try {
            for (javax.swing.UIManager.LookAndFeelInfo info : javax.swing.UIManager.getInstalledLookAndFeels()) {
                if ("Nimbus".equals(info.getName())) {
                    javax.swing.UIManager.setLookAndFeel(info.getClassName());
                    break;
                }
            }
        } catch (ClassNotFoundException ex) {
            java.util.logging.Logger.getLogger(Linked_list_UI.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (InstantiationException ex) {
            java.util.logging.Logger.getLogger(Linked_list_UI.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (IllegalAccessException ex) {
            java.util.logging.Logger.getLogger(Linked_list_UI.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (javax.swing.UnsupportedLookAndFeelException ex) {
            java.util.logging.Logger.getLogger(Linked_list_UI.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        }
        //</editor-fold>

        /* Create and display the form */
        java.awt.EventQueue.invokeLater(new Runnable() {
            public void run() {
                new Linked_list_UI().setVisible(true);
            }
        });
    }

    // Variables declaration - do not modify//GEN-BEGIN:variables
    private javax.swing.JMenu Edit_menu;
    private javax.swing.JFrame File;
    private javax.swing.JMenu File_menu;
    private javax.swing.JMenuItem Import_button;
    private javax.swing.JMenuItem Save;
    private javax.swing.JMenuItem SaveAs;
    private javax.swing.JTextField box_city;
    private javax.swing.JTextField box_first;
    private javax.swing.JTextField box_id;
    private javax.swing.JTextField box_last;
    private javax.swing.JTextField box_state;
    private javax.swing.Box.Filler filler1;
    private javax.swing.Box.Filler filler2;
    private javax.swing.Box.Filler filler3;
    private javax.swing.Box.Filler filler4;
    private javax.swing.JButton jButton1;
    private javax.swing.JButton jButton3;
    private javax.swing.JButton jButton4;
    private javax.swing.JButton jButton5;
    private javax.swing.JButton jButton6;
    private javax.swing.JFileChooser jFileChooser1;
    private javax.swing.JLabel jLabel1;
    private javax.swing.JLabel jLabel2;
    private javax.swing.JLabel jLabel3;
    private javax.swing.JLabel jLabel4;
    private javax.swing.JLabel jLabel5;
    private javax.swing.JMenuBar jMenuBar1;
    private javax.swing.JPanel jPanel1;
    private javax.swing.JScrollPane jScrollPane1;
    private javax.swing.JTable table;
    // End of variables declaration//GEN-END:variables
}
