# linux-dev-setup

Create a new Linux development environment, tailored to your needs. This setup includes:

1. **Create User:**
   - Creates a new user with customizable details.

2. **Essentials Package Dependencies:**
   - Installs essential package dependencies commonly required for development.

3. **Pyenv:**
   - Installs [Pyenv](https://github.com/pyenv/pyenv), a simple Python version management tool.

4. **Pipenv:**
   - Installs [Pipenv](https://pipenv.pypa.io/en/latest/), a packaging tool for Python projects.

## Requirements

1. **Docker:**
   - Ensure Docker is installed on your machine to run the development environment in a container.

2. **Ansible:**
   - Install Ansible on your local machine to configure the Ubuntu instance within the Docker container.

3. **Python:**
   - Python is required for Ansible. Ensure it's installed on your local machine.

## Setup

### Try it out in a docker container

1. **Create Docker Container:**
   - Use the following command to bring up the Docker container:
     ```bash
     docker-compose up
     ```
   - This command initializes the development environment inside a Docker container.

2. **Configure Ubuntu Instance with Ansible:**
   - Run the Ansible playbook to set up the Ubuntu instance within the Docker container:
     ```bash
     ansible-playbook -i local-docker create_user_playbook.yml
     >> Enter username: <username> # In this playbook the password of the user will be the <username>
     ansible-playbook -i local-docker dev_setup_playbook.yml --become-user <username> --ask-become-pass
     >> BECOME password: <username>
     ```
   - These playbooks create a new user, installs essential package dependencies, Pyenv, and Pipenv.

3. **Start Developing:**
   - Once the setup is complete, your development environment is ready.
   - Access the container with `docker exec -it ubuntu bash` and start coding!

### Execute it on your own local machine

Beware that executing this will require sudo privilege.

1. **Configure localhost with Ansible**
   ```bash
   ansible-playbook -i localhost dev_setup_playbook.yml --become-user <your-local-username> --ask-become-pass
   >> BECOME password: <sudo-password>
   ```

2. **Check configuration**
   ```bash
   pyenv --version
   >> * system (set by /home/<youe-local-username>/.pyenv/version)
   ```

## Customization

Feel free to customize the Ansible playbook (`main_playbook.yml`) to match your specific development requirements. Adjust package dependencies, Python versions, or additional tools as needed.

Enjoy your newly created Linux development environment!