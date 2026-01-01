📆 Day 3 – Docker, Kafka & AI Logs Analysis 🐝

Goal: Understand multi-track system setup: security, big data reliability, and AI anomaly detection.

🟦 [Security] – Docker on Windows 🐳
What I did

Tried running Python honeypot directly on Windows → multiple dependency issues.

Switched to Docker to simulate a Linux environment.

Verified containers can start and run logs without Windows-native conflicts.

Problems / Insights
Problem	Cause	Fix / Insight
Missing Python modules on Windows	Local environment not fully compatible	Docker provides isolated Linux environment
Version conflicts (Flask, Werkzeug)	Windows pip installs latest versions	Docker image pins working versions
External services fail	OS differences	Docker handles system dependencies

📌 Lesson: Docker solves Windows-native environment problems, making your multi-service apps portable and predictable. ✅

🟦 [Big Data] – Kafka & Log Integrity 📊
What I did

Investigated Kafka consumer-producer log flow.

Learned about message acknowledgments (ACKs).

Problems / Insights
Concept	Why it matters
ACK=0 (no ack)	Messages may be lost if consumer fails
ACK=1 (leader ack)	Only leader confirms → some risk if leader fails
ACK=all (full commit)	Guarantees all replicas store the message → ensures log completeness

📌 Lesson: Kafka ACK mechanism is key to ensuring log integrity in distributed systems. Even if some consumer crashes, logs are safe.

🟦 [AI] – Elasticsearch + Isolation Forest Anomaly Detection 🤖
What I did

Connected to local Elasticsearch instance:

es = Elasticsearch("http://localhost:9200")


Pulled honeypot logs (16 entries) and converted to pandas DataFrame:

data = [hit['_source'] for hit in res['hits']['hits']]
df = pd.DataFrame(data)


Added numeric features for AI:

df['event_num'] = pd.factorize(df['event'])[0]
df['timestamp_num'] = pd.to_datetime(df['timestamp']).astype(int) // 10**9


Used Isolation Forest to detect anomalies:

clf = IsolationForest(contamination=0.05, random_state=42)
clf.fit(df[['event_num','timestamp_num']])
df['anomaly'] = clf.predict(df[['event_num','timestamp_num']])

Problems / Fixes
Error / Issue	Cause	Fix / Insight
ModuleNotFoundError: elasticsearch	Missing package	Installed with pip install elasticsearch==8.10.0
BadRequestError 400 (media_type)	Elasticsearch 9 client incompatible with ES 8	Downgraded client to 8.10.0
Empty DataFrame / key errors	Columns mismatch (event_type vs event)	Checked df.columns → used correct column names
Type warning (factorize)	Using list instead of Series	Converted to Series
No anomalies detected initially	Only test log entries	Added simulated attack_log → detected correctly
Results

Successfully detected anomaly:

event	timestamp	anomaly
attack_log	2025-12-26T05:00:00.000000	-1

📸 Screenshots to include:

![DataFrame Preview](./day3/day3_df_preview.png)
![Anomaly Detected](./day3/day3_anomaly.png)

🐞 Key Insights

Isolation Forest works well on numeric features extracted from logs.

Always inspect DataFrame columns first before analysis.

External systems (Elasticsearch) must match the client version.

Simulated logs are useful for testing AI detection before real attacks occur.

🏁 Final Reflection

Today I realized multi-track analysis requires combining:

Secure environment (Docker)

Reliable data transport (Kafka ACKs)

Automated AI analysis (Isolation Forest)

Errors are not failures, they are learning points for proper system setup. 🔧

Adding screenshots to GitHub proves the workflow worked.