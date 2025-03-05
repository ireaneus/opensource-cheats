Here’s a **Splunk Cheatsheet** in **Markdown format** for quick reference. You can copy and use it as needed. 🚀  

---

# Splunk Cheat Sheet

## 📌 Basic Search Syntax
```sh
index=myindex sourcetype=access_combined
```
- `index=myindex` → Searches within a specific index.
- `sourcetype=access_combined` → Filters by sourcetype.

```sh
index=_internal earliest=-15m latest=now
```
- `earliest=-15m` → Search last 15 minutes.
- `latest=now` → Search up to the current time.

---

## 🎯 Common Search Commands
| Command | Description |
|---------|-------------|
| `index=main` | Searches all data in the main index. |
| `host="server1"` | Filters results from a specific host. |
| `source="/var/log/syslog"` | Filters events from a specific file. |
| `sourcetype="access_combined"` | Filters events by sourcetype. |
| `fieldname="value"` | Searches for events where `fieldname` has `value`. |
| `AND, OR, NOT` | Logical operators. |
| `"` `"search phrase"` | Searches for an exact phrase. |

---

## 🔍 Field Extraction
```sh
index=myindex | table host, source, sourcetype
```
- Displays a table with selected fields.

```sh
index=myindex | fields host, source
```
- Keeps only specified fields.

```sh
index=myindex | dedup host
```
- Removes duplicate values for `host`.

---

## 📊 Stats and Aggregations
```sh
index=myindex | stats count by host
```
- Counts events grouped by `host`.

```sh
index=myindex | stats avg(response_time) by host
```
- Calculates the average `response_time` for each `host`.

```sh
index=myindex | stats max(cpu_usage), min(cpu_usage) by host
```
- Finds max and min CPU usage per `host`.

---

## ⏳ Time-Based Searches
```sh
index=myindex earliest=-24h latest=now
```
- Searches the last 24 hours.

```sh
index=myindex earliest=-7d@d latest=@d
```
- Searches the last 7 days, aligning to the beginning of the day.

```sh
index=myindex | timechart span=1h count
```
- Creates an hourly timechart of event counts.

---

## 📈 Visualization Commands
```sh
index=myindex | timechart span=1d count by host
```
- Generates a daily trend by `host`.

```sh
index=myindex | chart count by host
```
- Creates a simple bar chart.

---

## 🔗 Joins and Subsearches
```sh
index=web_logs | join user_id [ search index=users ]
```
- Joins web logs with user data based on `user_id`.

```sh
index=main [ search index=errors | fields session_id ]
```
- Subsearch to match `session_id` in `index=main`.

---

## 📌 Alerts and Scheduled Searches
```sh
index=main error | stats count by host | where count > 10
```
- Alerts when `error` count exceeds 10 per `host`.

```sh
index=network | stats avg(latency) by host | where avg(latency) > 200
```
- Alerts when average latency is greater than 200ms.

---

## 📂 Log Parsing and Regex
```sh
index=myindex | rex field=_raw "User=(?<username>\S+)"
```
- Extracts `username` from raw logs.

```sh
index=myindex | regex _raw="ERROR|FAIL"
```
- Filters events containing `ERROR` or `FAIL`.

---

## 📑 Transactions
```sh
index=firewall | transaction src_ip maxpause=30s
```
- Groups events by `src_ip` with a max pause of 30 seconds.

---

## 📋 Useful Splunk Commands
| Command | Description |
|---------|-------------|
| `table field1, field2` | Displays results in table format. |
| `sort - field` | Sorts results in descending order. |
| `top field` | Finds most common values of a field. |
| `rare field` | Finds least common values of a field. |
| `eval new_field=value*100` | Creates a new calculated field. |

---

## ⚡ Performance Optimization Tips
```sh
index=myindex | fields - unnecessary_field
```
- Exclude unnecessary fields to improve search speed.

```sh
index=myindex | tstats count where index=* by host
```
- Use `tstats` for faster searches in large datasets.

```sh
index=myindex | bin _time span=1h | stats count by _time
```
- Use `bin` to aggregate events over time efficiently.

---

## 🔗 Useful Splunk Resources
- [Splunk Docs](https://docs.splunk.com/)
- [Splunk Query Examples](https://docs.splunk.com/Documentation/SCS/current/SearchReference/Examples)
- [Splunk Security Use Cases](https://www.splunk.com/en_us/solutions/solution-areas/security.html)

---

