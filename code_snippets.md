```python
import requests
import json

def fetch_all_leagues(url):
    response = requests.get(url)
    data = response.json()
    return data.get("leagues", [])

def save_leagues_to_file(leagues, filename):
    with open(filename, "w") as f:
        for league in leagues:
            f.write(league["strLeague"] + "\n")

def main():
    url = "https://www.thesportsdb.com/api/v1/json/3/all_leagues.php"
    leagues = fetch_all_leagues(url)
    save_leagues_to_file(leagues, "leagues.txt")

if __name__ == "__main__":
    main()
```

===

```python
import paramiko

# Server information
hostname = "10.10.10.10"
port = 22
username = "root"
password = "root"

try:
    # Create an SSH client
    ssh_client = paramiko.SSHClient()
    ssh_client.load_system_host_keys()
    
    # Automatically add the server's host key (this is insecure, do this only for testing)
    ssh_client.set_missing_host_key_policy(paramiko.AutoAddPolicy())
    
    try:
        # Connect to the server
        ssh_client.connect(hostname, port, username, password)
    except paramiko.AuthenticationException:
        print("Authentication failed, please check your credentials.")
        # Exit or handle the error as needed
    except paramiko.SSHException as e:
        print("SSH error:", str(e))
        # Exit or handle the error as needed
    
    # You are now connected. You can execute commands or perform other actions here.
    # For example, you can run the "ls -l" command and redirect the output to a file:
    command = "ls -l > example.txt"
    ssh_client.exec_command(command)
    
    # When you're done, close the SSH connection
    ssh_client.close()

except Exception as e:
    print("An error occurred:", str(e))
```
