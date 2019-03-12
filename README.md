<table cellpadding="2">
<tbody>
<tr>
<td>
<h4>Area of Concern</h4>
</td>
<td>
<h4>Guiding Questions</h4>
</td>
<td>
<h4>Recommended Practice(s)</h4>
</td>
</tr>
<tr>
<td>Authentication and Authorization</td>
<td>
<ul>
<li>Are appropriate measures taken to limit the exposure of OAuth2 tokens?</li>
<li>Are appropriate measures taken to securely store and retrieve OAuth2 tokens?</li>
<li>Are there appropriate procedures in place to support the revocation of tokens if a breach is detected?</li>
</ul>
</td>
<td>
<ul>
<li>In multi-tenant SaaS applications, avoid exposing the shared client_secret to tenants.</li>
<li>For single-tenant SaaS applications, storing client_secret within individual instances is also not recommended, even if the instance backend is not directly accessible by customers. The reason is rotation of credentials will be problematic.</li>
<li>In multi-tenant SaaS applications, avoid exposing the instance&nbsp;refresh_token&nbsp;to tenants.</li>
<li>If a SaaS multi-tenant authentication proxy is used for on-prem apps, the token refresh should also be done the multi-tenant layer and not the on-prem instance. Also, authentication capabilities between the on-prem instance and the SaaS proxy should be provided to guarantee that access_tokens are not shipped to the wrong tenant.</li>
<li>Leverage an external service that handles encryption, e.g. AWS Secrets Manager, GCP KMS, Azure KeyVault, etc.</li>
</ul>
</td>
</tr>
<tr>
<td>Compliance</td>
<td>
<ul>
<li>Are appropriate measures taken to comply with regional data exports laws?</li>
</ul>
</td>
<td>
<ul>
<li>Ensure applications are in compliance with GDPR et al.</li>
</ul>
</td>
</tr>
<tr>
<td>Isolation</td>
<td>
<ul>
<li>Are appropriate measures taken to isolate tenant data?</li>
</ul>
</td>
<td>
<ul>
<li>In multi-tenant SaaS applications, choose the appropriate multi-tenancy architecture given the use-case and requirements, i.e. shared pool vs hybrid vs dedicated tables.</li>
<li>Does the app actually store customer data or only facilitate access to APIs and write data back to App Framework, e.g. API Explorer?</li>
</ul>
</td>
</tr>
<tr>
<td>Logging and Reporting</td>
<td>
<ul>
<li>Are appropriate measures taken to provide adequate error handling, messaging, logging and diagnostics sufficient for triaging, troubleshooting, debugging and root cause analysis (as it pertains to interaction with App Framework APIs)?</li>
<li>Are appropriate measures taken to facilitate the audit access to protected resources?</li>
<li>Does the application provide adequate error handling, messaging, logging and diagnostics sufficient for triaging, troubleshooting, debugging and root cause analysis (as it pertains to interaction with App Framework APIs)?</li>
</ul>
</td>
<td>
<ul>
<li>Log tenant interactions with App Framework APIs and OAuth2 credential store.</li>
</ul>
</td>
</tr>
<tr>
<td>Monitoring</td>
<td>
<ul>
<li>Are appropriate measures taken to monitor for anomalous behavior?</li>
<li>Does the application provide adequate error handling, messaging, logging and diagnostics sufficient for triaging, troubleshooting, debugging and root cause analysis (as it pertains to interaction with App Framework APIs)?</li>
</ul>
</td>
<td>
<ul>
<li>Use logging to help determine when tenants/users are misbehaving.</li>
</ul>
</td>
</tr>
<tr>
<td>Performance/Throttling</td>
<td>
<ul>
<li>Does the application interact with the App Framework APIs in the most efficient/conservative manner possible?</li>
<li>Does the application implement best practices around OAuth token refreshing and caching?</li>
<li>Does the application implement appropriate measures for respecting API rate limits and quotas enforced by the App Framework and take appropriate measures to notify/police users when their behavior is in danger of breaching API rate limits/quotas?</li>
</ul>
</td>
<td>
<ul>
<li>Perform queries/polls in the most efficient manner possible, e.g. following recommended/best practices.</li>
<li>Persist/cache and reuse data obtained from APIs whenever possible, to avoid redundant API calls.</li>
<li>Cache access tokens and make available to clients in shared store to limit number of times a refresh is required.</li>
<li>Cache refresh token and make available to clients in shared store to support rolling refresh tokens.</li>
</ul>
</td>
</tr>
<tr>
<td>Privacy and Risk</td>
<td>
<ul>
<li>Are appropriate measures taken to guard against data leakage?</li>
</ul>
</td>
<td>
<ul>
<li>Implement safe guards to mitigate leakage of sensitive data, i.e. customer data.</li>
</ul>
</td>
</tr>
</tbody>
</table>
