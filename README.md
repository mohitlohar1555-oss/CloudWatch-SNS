<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>CloudWatch + SNS | EC2 Monitoring</title>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, Helvetica, sans-serif;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            background: #f4f7fb;
            color: #172033;
            line-height: 1.6;
        }

        /* NAVBAR */
        nav {
            width: 100%;
            background: #111827;
            color: white;
            padding: 18px 7%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            z-index: 1000;
            box-shadow: 0 3px 15px rgba(0,0,0,0.2);
        }

        .logo {
            font-size: 22px;
            font-weight: bold;
        }

        .logo span {
            color: #ff9900;
        }

        nav ul {
            list-style: none;
            display: flex;
            gap: 25px;
        }

        nav ul li a {
            color: white;
            text-decoration: none;
            font-size: 14px;
            transition: 0.3s;
        }

        nav ul li a:hover {
            color: #ff9900;
        }

        /* HERO */
        .hero {
            min-height: 620px;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            padding: 80px 7%;
            background: linear-gradient(135deg, #111827, #1e293b, #334155);
            color: white;
        }

        .hero-content {
            max-width: 900px;
        }

        .badge {
            display: inline-block;
            padding: 8px 18px;
            border: 1px solid #ff9900;
            border-radius: 30px;
            color: #ff9900;
            margin-bottom: 20px;
            font-size: 14px;
            font-weight: bold;
        }

        .hero h1 {
            font-size: 55px;
            line-height: 1.15;
            margin-bottom: 20px;
        }

        .hero h1 span {
            color: #ff9900;
        }

        .hero p {
            max-width: 750px;
            margin: auto;
            font-size: 18px;
            color: #d1d5db;
        }

        .hero-buttons {
            margin-top: 35px;
        }

        .btn {
            display: inline-block;
            padding: 13px 25px;
            margin: 8px;
            border-radius: 8px;
            text-decoration: none;
            font-weight: bold;
            transition: 0.3s;
        }

        .btn-primary {
            background: #ff9900;
            color: #111827;
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(255,153,0,0.3);
        }

        .btn-secondary {
            border: 1px solid #64748b;
            color: white;
        }

        .btn-secondary:hover {
            background: white;
            color: #111827;
        }

        /* GENERAL */
        section {
            padding: 80px 7%;
        }

        .section-title {
            text-align: center;
            margin-bottom: 50px;
        }

        .section-title h2 {
            font-size: 38px;
            margin-bottom: 10px;
        }

        .section-title p {
            color: #64748b;
        }

        /* CARDS */
        .cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(230px, 1fr));
            gap: 25px;
        }

        .card {
            background: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 8px 25px rgba(15,23,42,0.08);
            transition: 0.3s;
            border-top: 4px solid #ff9900;
        }

        .card:hover {
            transform: translateY(-8px);
        }

        .icon {
            font-size: 40px;
            margin-bottom: 15px;
        }

        .card h3 {
            margin-bottom: 10px;
            font-size: 21px;
        }

        .card p {
            color: #64748b;
            font-size: 14px;
        }

        /* ARCHITECTURE */
        .architecture {
            background: #111827;
            color: white;
        }

        .architecture .section-title p {
            color: #cbd5e1;
        }

        .architecture-flow {
            max-width: 1100px;
            margin: auto;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
            flex-wrap: wrap;
        }

        .arch-box {
            background: #1e293b;
            border: 1px solid #475569;
            border-radius: 15px;
            width: 180px;
            min-height: 150px;
            padding: 25px 15px;
            text-align: center;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        .arch-box .icon {
            font-size: 38px;
        }

        .arrow {
            font-size: 35px;
            color: #ff9900;
            font-weight: bold;
        }

        /* PROCESS */
        .process {
            max-width: 1000px;
            margin: auto;
        }

        .step {
            display: flex;
            gap: 25px;
            margin-bottom: 25px;
            background: white;
            padding: 25px;
            border-radius: 12px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.06);
        }

        .step-number {
            min-width: 55px;
            height: 55px;
            border-radius: 50%;
            background: #ff9900;
            color: #111827;
            display: flex;
            justify-content: center;
            align-items: center;
            font-weight: bold;
            font-size: 20px;
        }

        .step h3 {
            margin-bottom: 5px;
        }

        .step p {
            color: #64748b;
        }

        /* CODE */
        .code-section {
            background: #0f172a;
            color: white;
        }

        .code-container {
            max-width: 1100px;
            margin: auto;
        }

        .code-box {
            background: #020617;
            padding: 25px;
            border-radius: 12px;
            overflow-x: auto;
            margin-bottom: 25px;
            border: 1px solid #334155;
        }

        .code-title {
            color: #ff9900;
            margin-bottom: 12px;
        }

        pre {
            color: #d1d5db;
            font-family: Consolas, monospace;
            font-size: 14px;
            white-space: pre-wrap;
        }

        /* ALARM */
        .alarm-box {
            max-width: 900px;
            margin: auto;
            background: white;
            padding: 40px;
            border-radius: 18px;
            box-shadow: 0 10px 35px rgba(0,0,0,0.08);
            text-align: center;
        }

        .cpu-meter {
            margin: 30px auto;
            max-width: 600px;
            height: 25px;
            background: #e5e7eb;
            border-radius: 20px;
            overflow: hidden;
        }

        .cpu-progress {
            width: 85%;
            height: 100%;
            background: #ef4444;
        }

        .alarm-status {
            display: inline-block;
            padding: 10px 20px;
            background: #fee2e2;
            color: #b91c1c;
            border-radius: 30px;
            font-weight: bold;
        }

        /* TABLE */
        table {
            width: 100%;
            border-collapse: collapse;
            background: white;
            box-shadow: 0 8px 25px rgba(0,0,0,0.07);
            border-radius: 12px;
            overflow: hidden;
        }

        th, td {
            padding: 17px;
            text-align: left;
            border-bottom: 1px solid #e5e7eb;
        }

        th {
            background: #111827;
            color: white;
        }

        td {
            color: #475569;
        }

        /* OUTCOME */
        .outcome {
            background: linear-gradient(135deg, #fff7ed, #fef3c7);
        }

        .outcome-box {
            max-width: 900px;
            margin: auto;
            text-align: center;
            background: white;
            padding: 45px;
            border-radius: 20px;
            box-shadow: 0 10px 35px rgba(0,0,0,0.08);
        }

        .outcome-box h2 {
            font-size: 35px;
            margin-bottom: 20px;
        }

        .outcome-box p {
            color: #64748b;
            margin-bottom: 25px;
        }

        .skills {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 12px;
        }

        .skill {
            background: #111827;
            color: white;
            padding: 9px 18px;
            border-radius: 30px;
            font-size: 13px;
        }

        /* FOOTER */
        footer {
            background: #020617;
            color: #94a3b8;
            text-align: center;
            padding: 35px 20px;
        }

        footer strong {
            color: #ff9900;
        }

        /* RESPONSIVE */
        @media(max-width: 768px) {

            nav {
                flex-direction: column;
                gap: 15px;
            }

            nav ul {
                flex-wrap: wrap;
                justify-content: center;
                gap: 12px;
            }

            .hero h1 {
                font-size: 38px;
            }

            .hero p {
                font-size: 16px;
            }

            .arrow {
                transform: rotate(90deg);
            }

            .step {
                flex-direction: column;
            }

            table {
                font-size: 13px;
            }

            th, td {
                padding: 10px;
            }
        }
    </style>
</head>

<body>

<!-- NAVBAR -->
<nav>

    <div class="logo">
        ☁️ <span>AWS</span> Monitoring
    </div>

    <ul>
        <li><a href="#home">Home</a></li>
        <li><a href="#services">Services</a></li>
        <li><a href="#architecture">Architecture</a></li>
        <li><a href="#process">Process</a></li>
        <li><a href="#commands">Commands</a></li>
        <li><a href="#outcome">Outcome</a></li>
    </ul>

</nav>


<!-- HERO -->
<section class="hero" id="home">

    <div class="hero-content">

        <div class="badge">
            AWS DEVOPS PROJECT
        </div>

        <h1>
            EC2 Monitoring using
            <span>CloudWatch + SNS</span>
        </h1>

        <p>
            A complete AWS monitoring and alerting solution that monitors
            EC2 CPU utilization using Amazon CloudWatch and sends
            real-time email notifications through Amazon SNS.
        </p>

        <div class="hero-buttons">

            <a href="#architecture" class="btn btn-primary">
                View Architecture
            </a>

            <a href="#commands" class="btn btn-secondary">
                View Commands
            </a>

        </div>

    </div>

</section>


<!-- SERVICES -->
<section id="services">

    <div class="section-title">

        <h2>AWS Services Used</h2>

        <p>
            Technologies used in this monitoring project
        </p>

    </div>


    <div class="cards">

        <div class="card">

            <div class="icon">🖥️</div>

            <h3>Amazon EC2</h3>

            <p>
                Provides the Linux-based virtual server whose
                CPU utilization is monitored.
            </p>

        </div>


        <div class="card">

            <div class="icon">📊</div>

            <h3>Amazon CloudWatch</h3>

            <p>
                Collects EC2 monitoring metrics and evaluates
                configured alarm conditions.
            </p>

        </div>


        <div class="card">

            <div class="icon">🔔</div>

            <h3>Amazon SNS</h3>

            <p>
                Sends notification messages to subscribed
                endpoints such as email.
            </p>

        </div>


        <div class="card">

            <div class="icon">📧</div>

            <h3>Email</h3>

            <p>
                Receives the CloudWatch alarm notification
                through the SNS subscription.
            </p>

        </div>

    </div>

</section>


<!-- ARCHITECTURE -->
<section class="architecture" id="architecture">

    <div class="section-title">

        <h2>Project Architecture</h2>

        <p>
            How CloudWatch and SNS work together
        </p>

    </div>


    <div class="architecture-flow">

        <div class="arch-box">

            <div class="icon">🖥️</div>

            <h3>EC2</h3>

            <p>CPU Utilization</p>

        </div>


        <div class="arrow">
            →
        </div>


        <div class="arch-box">

            <div class="icon">📊</div>

            <h3>CloudWatch</h3>

            <p>Metric Monitoring</p>

        </div>


        <div class="arrow">
            →
        </div>


        <div class="arch-box">

            <div class="icon">🚨</div>

            <h3>Alarm</h3>

            <p>CPU &gt; 70%</p>

        </div>


        <div class="arrow">
            →
        </div>


        <div class="arch-box">

            <div class="icon">🔔</div>

            <h3>SNS</h3>

            <p>Notification</p>

        </div>


        <div class="arrow">
            →
        </div>


        <div class="arch-box">

            <div class="icon">📧</div>

            <h3>Email</h3>

            <p>Alert Received</p>

        </div>

    </div>

</section>


<!-- PROCESS -->
<section id="process">

    <div class="section-title">

        <h2>Complete Process</h2>

        <p>
            Step-by-step implementation
        </p>

    </div>


    <div class="process">

        <div class="step">

            <div class="step-number">1</div>

            <div>

                <h3>Launch EC2 Instance</h3>

                <p>
                    Launch an Amazon Linux EC2 instance and make
                    sure the instance is running.
                </p>

            </div>

        </div>


        <div class="step">

            <div class="step-number">2</div>

            <div>

                <h3>Create SNS Topic</h3>

                <p>
                    Create an SNS topic named
                    <b>EC2-CPU-Alert</b> to receive CloudWatch
                    alarm notifications.
                </p>

            </div>

        </div>


        <div class="step">

            <div class="step-number">3</div>

            <div>

                <h3>Create Email Subscription</h3>

                <p>
                    Subscribe your email address to the SNS topic
                    and confirm the subscription from your email.
                </p>

            </div>

        </div>


        <div class="step">

            <div class="step-number">4</div>

            <div>

                <h3>Create CloudWatch Alarm</h3>

                <p>
                    Configure a CloudWatch alarm for the EC2
                    CPUUtilization metric with a threshold of 70%.
                </p>

            </div>

        </div>


        <div class="step">

            <div class="step-number">5</div>

            <div>

                <h3>Connect CloudWatch to SNS</h3>

                <p>
                    Configure the SNS topic as the alarm action.
                    When the alarm enters ALARM state, CloudWatch
                    publishes a notification to SNS.
                </p>

            </div>

        </div>


        <div class="step">

            <div class="step-number">6</div>

            <div>

                <h3>Generate CPU Load</h3>

                <p>
                    Generate CPU utilization on the EC2 instance
                    to test the monitoring and alerting system.
                </p>

            </div>

        </div>


        <div class="step">

            <div class="step-number">7</div>

            <div>

                <h3>Receive Email Alert</h3>

                <p>
                    When CPU utilization crosses the configured
                    threshold, CloudWatch triggers the alarm and
                    SNS sends an email notification.
                </p>

            </div>

        </div>

    </div>

</section>


<!-- ALARM STATUS -->
<section>

    <div class="section-title">

        <h2>CloudWatch Alarm Simulation</h2>

        <p>
            Example of an EC2 high CPU condition
        </p>

    </div>


    <div class="alarm-box">

        <h3>EC2 CPU Utilization</h3>

        <h1>85%</h1>

        <div class="cpu-meter">

            <div class="cpu-progress"></div>

        </div>

        <p>
            Threshold configured:
            <strong>70%</strong>
        </p>

        <br>

        <div class="alarm-status">
            🚨 ALARM
        </div>

        <br><br>

        <p>
            CloudWatch detects that CPU utilization is above
            the configured threshold and sends the alarm
            notification to SNS.
        </p>

    </div>

</section>


<!-- COMMANDS -->
<section class="code-section" id="commands">

    <div class="section-title">

        <h2>Important AWS CLI Commands</h2>

        <p>
            Commands used for SNS and CloudWatch configuration
        </p>

    </div>


    <div class="code-container">


        <div class="code-box">

            <h3 class="code-title">
                01. Create SNS Topic
            </h3>

<pre>
aws sns create-topic --name EC2-CPU-Alert
</pre>

        </div>


        <div class="code-box">

            <h3 class="code-title">
                02. Subscribe Email
            </h3>

<pre>
aws sns subscribe \
--topic-arn &lt;SNS-TOPIC-ARN&gt; \
--protocol email \
--notification-endpoint your-email@example.com
</pre>

        </div>


        <div class="code-box">

            <h3 class="code-title">
                03. List SNS Subscriptions
            </h3>

<pre>
aws sns list-subscriptions-by-topic \
--topic-arn &lt;SNS-TOPIC-ARN&gt;
</pre>

        </div>


        <div class="code-box">

            <h3 class="code-title">
                04. Create CloudWatch Alarm
            </h3>

<pre>
aws cloudwatch put-metric-alarm \
--alarm-name "EC2-High-CPU" \
--alarm-description "Alarm when EC2 CPU exceeds 70 percent" \
--metric-name CPUUtilization \
--namespace AWS/EC2 \
--statistic Average \
--period 300 \
--threshold 70 \
--comparison-operator GreaterThanThreshold \
--evaluation-periods 1 \
--alarm-actions &lt;SNS-TOPIC-ARN&gt; \
--dimensions Name=InstanceId,Value=&lt;INSTANCE-ID&gt;
</pre>

        </div>


        <div class="code-box">

            <h3 class="code-title">
                05. Check Alarm
            </h3>

<pre>
aws cloudwatch describe-alarms \
--alarm-names EC2-High-CPU
</pre>

        </div>


        <div class="code-box">

            <h3 class="code-title">
                06. Test SNS Notification
            </h3>

<pre>
aws sns publish \
--topic-arn &lt;SNS-TOPIC-ARN&gt; \
--subject "Test EC2 Alert" \
--message "Testing AWS SNS notification."
</pre>

        </div>


        <div class="code-box">

            <h3 class="code-title">
                07. Generate CPU Load
            </h3>

<pre>
sudo yum install stress -y

stress --cpu 2 --timeout 600
</pre>

        </div>


    </div>

</section>


<!-- CONFIGURATION TABLE -->
<section>

    <div class="section-title">

        <h2>CloudWatch Alarm Configuration</h2>

        <p>
            Example configuration used in this project
        </p>

    </div>


    <table>

        <tr>
            <th>Configuration</th>
            <th>Value</th>
        </tr>

        <tr>
            <td>Metric</td>
            <td>CPUUtilization</td>
        </tr>

        <tr>
            <td>Namespace</td>
            <td>AWS/EC2</td>
        </tr>

        <tr>
            <td>Statistic</td>
            <td>Average</td>
        </tr>

        <tr>
            <td>Period</td>
            <td>5 Minutes</td>
        </tr>

        <tr>
            <td>Threshold</td>
            <td>70%</td>
        </tr>

        <tr>
            <td>Comparison</td>
            <td>Greater Than Threshold</td>
        </tr>

        <tr>
            <td>Action</td>
            <td>SNS Notification</td>
        </tr>

        <tr>
            <td>Notification</td>
            <td>Email</td>
        </tr>

    </table>

</section>


<!-- OUTCOME -->
<section class="outcome" id="outcome">

    <div class="outcome-box">

        <h2>🎯 Project Outcome</h2>

        <p>
            Successfully implemented an automated EC2 monitoring
            and alerting system using Amazon CloudWatch and Amazon SNS.
            The system detects high CPU utilization and automatically
            sends an email notification to the configured recipient.
        </p>


        <div class="skills">

            <span class="skill">AWS EC2</span>

            <span class="skill">CloudWatch</span>

            <span class="skill">SNS</span>

            <span class="skill">Linux</span>

            <span class="skill">AWS CLI</span>

            <span class="skill">Monitoring</span>

            <span class="skill">Alerting</span>

            <span class="skill">DevOps</span>

        </div>

    </div>

</section>


<!-- FOOTER -->
<footer>

    <p>
        Designed for an AWS DevOps Cloud Engineer Project
    </p>

    <p>
        <strong>EC2 + CloudWatch + SNS</strong>
    </p>

    <p>
        © 2026 Cloud Monitoring Project
    </p>

</footer>


</body>
</html>
