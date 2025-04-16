# 🍽️ Chef & 🐶 Puppet Summary

## What Are They?
Both **Chef** and **Puppet** are **Configuration Management (CM)** tools used to automate infrastructure provisioning, enforce system states, and ensure consistency across environments.

---

## 🐶 Puppet

### Overview
- **Declarative language** written in Puppet DSL (domain-specific language)
- Uses **agent/master model** (can be agentless with Bolt)
- Developed by **Puppet Inc.**
- Great for **enforcing desired system state**

### Architecture
- **Puppet Master**: Central server with the logic
- **Puppet Agent**: Installed on target nodes
- Uses **Facter** to collect system facts

### Key Concepts
- **Manifests**: Files that define system configuration (`.pp` files)
- **Modules**: Reusable units of Puppet code
- **Resources**: Define specific aspects (e.g., package, service, file)

### Sample Code
```puppet
package { 'nginx':
  ensure => installed,
}

service { 'nginx':
  ensure => running,
  enable => true,
}
```

---

## 🍽️ Chef

### Overview
- Uses **Ruby-based DSL**
- More **imperative** than Puppet
- Developed by **Progress Software**
- Favors **code over configuration**

### Architecture
- **Chef Server**: Central hub of configurations
- **Chef Workstation**: Where cookbooks are authored
- **Chef Client**: Runs on target nodes
- **Ohai**: Gathers node data like Facter in Puppet

### Key Concepts
- **Cookbooks**: Containers for configuration policies
- **Recipes**: Inside cookbooks, contain actual config logic
- **Resources**: Describe the desired state
- **Run Lists**: Ordered list of recipes/roles to apply

### Sample Code
```ruby
package 'nginx'

service 'nginx' do
  action [:enable, :start]
end
```

---

## Comparison

| Feature        | Puppet                   | Chef                     |
|----------------|--------------------------|--------------------------|
| Language       | Puppet DSL (declarative) | Ruby DSL (imperative)    |
| Server Model   | Master/Agent             | Server/Client            |
| Learning Curve | Easier for beginners     | Flexible but steeper     |
| Push/Pull      | Pull-based               | Pull-based               |
| Idempotency    | Yes                      | Yes                      |
| Node Info      | Facter                   | Ohai                     |

---

> ⚙️ _Use these tools when you need to scale config changes across multiple systems reliably._
