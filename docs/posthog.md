## Posthog for your application

PostHog is an open-source product analytics suite, built for engineers that can automatically track every event on your website or app. Based on these events, it can help you understand your users and how to improve your product. 

An organization can have multiple mobile and web-apps running at the same time. We can have one Posthog setup configured for all these different applications within the organization. Posthog will capture the events for all the applications and separate them within different sections.

### Prerequisites for setup on Digital Ocean

1. Application Domain and DNS details
2. Digital Ocean account
3. Some knowledge of Kubernetes
4. Helm package manager
5. Operating System - Windows/Linux/Mac OS

## Setting up Posthog on Digital Ocean:

First, we have to add the website DNS addresses to the Digital Ocean account. To do that, you just have to point the DNS nodes in the domain on the DigitalOcean dashboard, Digital ocean has some DNS points such as DNS1, DNS2, DNS3. You simply have to put your website DNS values into these textfields.

Follow these steps in order to [Set up DNS and Digital Ocean](https://docs.digitalocean.com/products/networking/dns/quickstart/). To verify the setup, click [here](https://dnschecker.org/)

1. Create a Kubernetes Cluster with at least 4 nodes. If you have a Digital Ocean account, just click [here](https://cloud.digitalocean.com/kubernetes/clusters/) to directly create a new cluster. Provide a name to the cluster. Optionally, you can provide some tags for your cluster as well.

The following image shows what a sample kubernetes cluster looks like:

<p align="center">
<img src="https://user-images.githubusercontent.com/77961530/182447425-a1a55f5b-7190-4967-87be-7ae50e2a492d.png" width="600"/>
</p>
2. Once you create a Cluster, click on the newly created cluster. Inside the cluster, Navigate to the "Marketplace" section. Under the "Install Kubernetes 1-Click Apps" search Posthog. The following drop down list should show Posthog, click on the option to download Posthog for your application cluster instance.

<p align="center">
<img src="https://user-images.githubusercontent.com/77961530/182447548-08dc8314-3a57-4153-a620-0c10787226e8.png" width="600"/>
</p>

3. For the next step, you have to modify the "values.yml" file with your custom domain names.

```yaml
cloud: "do"
ingress:
  hostname: telemetry.shikshaplatform.io
  nginx:
    enabled: true
cert-manager:
  enabled: true
ingress-nginx:
  controller:
    config:
      use-proxy-protocol: true
    service:
      annotations:
        service.beta.kubernetes.io/do-loadbalancer-hostname: telemetry.shikshaplatform.io
        service.beta.kubernetes.io/do-loadbalancer-enable-proxy-protocol: "true"
```

In both Line 3 and Line 15, the values "hostname" and "service.beta.kubernetes.io/do-loadbalancer-hostname" are updated to include the organization domain names.

4. The next step is to download the Config file for your cluster. This config file is present inside the Overview section under the "Configuration" option.

5. Add the path link for the Config file inside the following the following command:

```shell
helm repo add posthog https://posthog.github.io/charts-clickhouse/
```

6. Update the repository

```shell
helm repo update
```

7. Update the following command with your custom DNS addresses which point you towards the DNS server. These domain values must be the same as provided in the Step 2:

```shell
helm upgrade -f values.yaml --timeout 20m --namespace posthog posthog posthog/posthog --atomic --wait --wait-for-jobs --debug
```

The above command will automatically generate sort of an IP address for you.

8. Executing the above command will generate an IP on your DigitalOcean Dashboard under the “Directs to” drop down menu. Now, we have to just point that IP towards our desired Kubernetes cluster.

9. Finally, executing the following command will convert the IP into a secure HTTPS URL.

```shell
kubectl apply -f cluster-issuer.yaml
```

10. Check the host

```shell
bash getHost.sh
```

## Posthog self-setup instructions

Self hosting and running a production environment of Posthog is one of the most important steps to take as a developer. The following docs go through how to Self host an instance of Posthog and various deployment options it provides. To view all these steps, click [here](https://posthog.com/docs/self-host).

## Setting up environment variables for your application

In posthog, you can set the values through both Instance settings as well as Environment variables. Though Instance settings is recommended for most applications, you can also set the values for your application using Environment variables. There are various environment variables you can set for your application instance. To get a detailed explanation of what each variable does and how to configure it, click [here](https://posthog.com/docs/self-host/configure/environment-variables).

## Using Posthog

### 1. How to View 

To view various events and get insights related to how your applications is performing you can navigate to the Posthog dashboard and under "Insights" section. After connecting your application with Posthog and configuring the relevant settings, you can view the dashboard by clicking on the created cluster. In Insights, you can view what events your visitors are performing and get a detailed performance review for your application. For example:

<p align="center">
<img src="https://user-images.githubusercontent.com/77961530/182447548-08dc8314-3a57-4153-a620-0c10787226e8.png" width="600"/>
</p>

### 2. What Can be Done?

1. Session recording - Session Recording allows you to record users navigating through your website and play back the individual sessions to watch how real users use your product. You can get various details such as duration, start point, end point and you can also replay these recordings in order to understand if the visitors are spending unusual amount of time stuck in a particular section on a website. These details help you improve the overall quality of your application. This is how the recorded sessions looks like:

<p align="center">
<img width="600" alt="recording" src="https://user-images.githubusercontent.com/77961530/182457927-91e9a9bf-9a02-4e0e-ac09-68b1b74a0705.png">
</p>

2. Feature flags - Feature Flags allow you to safely deploy and roll back new features. This means you can ship the code for new features and then roll them out to your users in a managed way. If something has goes wrong, you can then roll back without having to re-deploy your application. Feature Flags can also help you control access to certain parts of your product, such as only showing paid features to users with an active subscription.

<p align="center">
<img width="600" alt="feature-flags" src="https://user-images.githubusercontent.com/77961530/182458542-30de04ee-39fd-44fa-9ee7-4b5d23af0238.png">
</p>

3. Posthog A/B testing - It allows us to compare two versions of something to figure out which performs better. It’s most often associated with websites and apps. Posthog provides us with its own Experimentation suite to see the performance of various modules. To see how it works, click [here](https://posthog.com/product/experimentation-suite). Following image shows some posthog A/B testing tools:

<p align="center">
<img width="600" alt="test-tools" src="https://user-images.githubusercontent.com/77961530/182459414-89957ce6-c818-441b-9eec-ded3e5250ce4.png">
</p>

Along with this, Posthog also allows service such as Event pipelines, Self hosting, Data warehouses, Various APIs to integrate and configure the event pipelines. To see them in detail, click [here](https://posthog.com/?utm_source=kdnuggets&utm_medium=sponsored-blog&utm_campaign=23-sept-2021)
