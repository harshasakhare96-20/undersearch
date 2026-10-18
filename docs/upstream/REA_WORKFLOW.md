# Optional REA workflow for AEO research

REA is a separate local agent toolkit, not a service dependency. Its website analysis can help an operator inspect an authorized site's page structure, scripts, network observations, and screenshots when diagnosing crawl or content-access issues.

Use it only for sites you own or have permission to assess. Keep evidence and limitations with any recommendation. Do not use REA to bypass access controls or platform protections, and do not infer answer-engine rankings from a website inspection.

To adopt REA separately, follow the current official instructions at [morluto/rea](https://github.com/morluto/rea). Its README currently describes `npx rea-agents setup` for registering the tools with supported agents. That setup changes local agent configuration, so review the proposed changes before accepting them. REA is not installed by this AEO repository and the application will work without it.
