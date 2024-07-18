# Step 1: Create a basic task with a name
![image](https://github.com/user-attachments/assets/b6b6df9c-94c0-4cc8-b32d-24748b845be6)

# Step 2: Set a schedule
![image](https://github.com/user-attachments/assets/4ab72eb6-e6d4-43e1-8b36-e9a12714a6bc)

# Step 3: Click "Start a program"
![image](https://github.com/user-attachments/assets/01ad8d66-6f17-4d23-ae0f-db8e46c1950c)

# Step 4: It will open the System32 directory, I then searched for "powershell.exe", click the right one
![image](https://github.com/user-attachments/assets/dfa1bdbd-7fbe-4b68-94ae-3506286f9015)

# Step 5: Input into arguments the code I provided above 

```PS1
Start-Process "C:\Users\YOURUSERNAME\Desktop\Backup SQL\backup_mariadb.bat"
```
This will trigger the powershell file which will trigger the bat file to the schedule that you set
![image](https://github.com/user-attachments/assets/0b93258a-f694-422b-bdc5-b56e2cebb9ef)

# Final step: Hit finish and then you should see it in your scheduler. 

TIP: You can right click and click run to see it do its thing. This would be classed as a test
![image](https://github.com/user-attachments/assets/f57375b8-a63b-47ad-a551-48d6bee8348c)
