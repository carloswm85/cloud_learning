# Azure recommended names

## Table of Contents

- [Azure recommended names](#azure-recommended-names)
  - [Table of Contents](#table-of-contents)
  - [(1) Naming pattern](#1-naming-pattern)
  - [(2) Examples](#2-examples)
  - [(3) Variations](#3-variations)
  - [(4) References](#4-references)

---

## (1) Naming pattern

The Azure Cloud Adoption Framework recommends building resource names from consistent components. A general pattern is:

`<resource-type>-<workload>-<environment>-<region>-<instance>`

Use only the components that help identify and operate the resource. A shorter pattern is sufficient when the region is not operationally useful:

`<resource-type>-<workload>-<environment>-<instance>`

Azure recommends `stapp` as the abbreviation for a Static Web App and `rg` for a resource group.

---

## (2) Examples

|   # | Resource       | Placeholder pattern                                         | Concrete example                   | Situation                                     |
| --: | -------------- | ----------------------------------------------------------- | ---------------------------------- | --------------------------------------------- |
|   1 | Resource group | `rg-<workload>-<environment>`                               | `rg-zen-garden-dev`                | ✅ Recommended for the lab                    |
|   2 | Static Web App | `stapp-<workload>-<environment>-<instance>`                 | `stapp-zen-garden-dev-001`         | ✅ Recommended default                        |
|   3 | Static Web App | `stapp-<workload>-<environment>-<region>-<instance>`        | `stapp-zen-garden-prod-eus2-001`   | 🤔 Include region when operationally useful   |
|   4 | Static Web App | `stapp-<workload>-<variant>-<environment>-<instance>`       | `stapp-zen-garden-angular-dev-001` | 🤔 Use when variants coexist                  |
|   5 | Static Web App | `stapp-<workload>-<environment>-<instance>-<unique-suffix>` | `stapp-zen-garden-dev-001-a7f3`    | 🤔 Use when the preferred name is unavailable |

---

## (3) Variations

- Use short environment names such as `dev`, `test`, `stg`, and `prod`.
- Keep framework names such as `angular` out of the normal name because the framework is an implementation detail. Include one as a variant only when, for example, plain HTML and Angular versions must coexist.
- Add a region abbreviation, such as `eus2` for East US 2, when the team operates resources across multiple regions. Use one documented regional abbreviation consistently.
- Use a zero-padded instance such as `001` when more than one instance might exist.
- Append a short deterministic suffix when global uniqueness requires it. Avoid personal, sensitive, or confidential information in resource names.
- Keep names lowercase and hyphen-separated for consistency, even when a resource type accepts additional characters.
- Store details that can change, such as the owner or cost center, in Azure tags instead of the resource name.

---

## (4) References

- <https://learn.microsoft.com/azure/cloud-adoption-framework/ready/azure-best-practices/resource-naming>
- <https://learn.microsoft.com/azure/cloud-adoption-framework/ready/azure-best-practices/resource-abbreviations>
