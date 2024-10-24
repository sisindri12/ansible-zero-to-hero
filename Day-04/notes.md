**Ansible Study Guide**

**Introduction to Ansible**
- Ansible is an open-source automation tool used for configuration management, application deployment, and task automation. It uses a simple language (YAML) to describe automation jobs.
- The series covers various aspects of Ansible, starting from the basics to more advanced concepts like roles and playbooks .

**Key Concepts**
1. **Ansible Playbooks**
   - A Playbook is a YAML file containing a list of plays. Each play defines the tasks to be executed on specified hosts .
   - Each play includes fields like:
     - **hosts**: Specifies which hosts to target.
     - **tasks**: A collection of actions to perform on the target hosts.
     - **variables**: Used to define values that can be reused throughout the playbook .

2. **Ansible Roles**
   - Roles are a way to organize playbooks into reusable components. They help improve readability and modularity by splitting playbooks into different sections (e.g., tasks, handlers, variables) .
   - To create a role, use the command: `ansible-galaxy role init <role_name>` .

3. **Folder Structure of Roles**
   - Each role typically contains several directories:
     - **tasks**: Contains the main tasks to be executed.
     - **handlers**: Tasks that are triggered by notifications from other tasks.
     - **vars**: Variables specific to the role.
     - **defaults**: Default values for variables .

**Example of a Playbook**
- A simple playbook might look like this:
```yaml
- name: Install Apache
  hosts: all
  tasks:
    - name: Install httpd
      yum:
        name: httpd
        state: present
    - name: Start httpd
      service:
        name: httpd
        state: started
```
- This playbook installs and starts the Apache web server on all specified hosts .

**Advantages of Using Roles**
- Roles enhance the organization of playbooks, making them easier to read and maintain.
- They allow for sharing and reusing code across different projects and teams .

**Dynamic vs. Static Files**
- **Static files**: Placed in the `files` directory and copied directly to the target machine.
- **Dynamic files**: Use templates (e.g., Jinja2) to allow variable substitution, making them adaptable to different environments .

**Handlers**
- Handlers are special tasks that only run when notified by other tasks. For example, if a configuration file changes, you might want to restart a service .

**Conclusion**
- Understanding Ansible's structure, including playbooks and roles, is crucial for effective automation. The modular approach provided by roles simplifies complex playbooks, making them easier to manage and share .