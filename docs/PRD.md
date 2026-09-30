# LocalHost --- Community-Government Digital Platform

**Status:** Product & Technical PRD\
**Product Type:** Multi-tenant civic/community platform\
**Technical Role:** Community-government digital infrastructure\
**Architecture:** Hierarchical, multi-tenant, source-agnostic,
serverless-first\
**Initial Stack:** Next.js + TypeScript + Supabase/PostgreSQL + Coolify

------------------------------------------------------------------------

## 1. Product Definition

LocalHost is a **community-government digital platform** that connects
residents, local administrative units, services, community information,
and existing institutional data sources.

LocalHost should be treated as:

-   **Product:** Platform
-   **Technical role:** Digital infrastructure
-   **Architecture:** Reusable framework/model
-   **Data philosophy:** Source-agnostic / Bring Your Own Data Source
    (BYODS)
-   **Deployment model:** Dukuh → Desa/Kelurahan → Kecamatan federation

LocalHost is not merely a mobile village-administration application. It
is intended to provide a reusable digital layer around existing local
administration, community information, services, and data.

------------------------------------------------------------------------

## 2. Executive Summary

The original LocalHost concept focused on hyperlocal mutual aid and
skill exchange. The initial problem statement identified limited
interaction between residents, especially in urban, boarding-house, and
apartment environments, while nearby residents may have useful time,
tools, goods, or skills. The proposed solution was a hyperlocal
mechanism for residents to request and offer help.

The concept has since expanded into a broader community-government
platform.

The broader problem is that local information and administrative data
are often fragmented across:

-   Excel files
-   Google Sheets
-   Google Drive
-   WhatsApp
-   paper/document systems
-   existing databases
-   government systems
-   individual administrators

Residents may need information about:

-   local services
-   facilities
-   administrative contacts
-   community announcements
-   population information where authorized
-   nearby resources
-   local assistance

Administrators may already have the necessary data but lack a unified
interface, search layer, verification workflow, contribution mechanism,
and community-facing services.

Therefore:

> **LocalHost acts as a digital layer between existing local
> data/institutions and the people who need to use that information and
> services.**

LocalHost should not require organizations to replace their existing
systems or migrate all data into a LocalHost-owned database.

------------------------------------------------------------------------

## 3. Source and Research Basis

The original project deck identified:

-   limited interaction among residents;
-   local needs that could potentially be solved by nearby residents;
-   residents with unused tools, time, or skills;
-   the need for a focused local mechanism for mutual aid;
-   resident search and filtering;
-   population information;
-   blood-type search;
-   village information;
-   service contacts;
-   privileged access;
-   contribution and contribution levels.

The deck also described RT/RW/WhatsApp and Google Maps as existing
alternatives, with LocalHost positioned around structured local
information.

The original MVP listed:

-   Login / Role Access
-   Data Penduduk
-   Search & Filter
-   Dashboard Map
-   Info Desa & Kontak
-   Forum Warga
-   Update / Koreksi Data
-   Contribution Point
-   Contribution Level

The platform architecture in this PRD expands those ideas into a
hierarchical community-government system while retaining mutual aid and
community contribution as modules.

------------------------------------------------------------------------

# 4. Vision

> **Make local communities easier to understand, serve, connect, and
> participate in through shared digital infrastructure.**

Long-term model:

``` text
Existing Institutions
        +
Existing Data
        +
Local Government
        +
Community
        ↓
     LocalHost
        ↓
Structured Local Digital Environment
```

------------------------------------------------------------------------

# 5. Problem Statement

## 5.1 Community Problem

Residents can have local needs that are difficult to solve because they
do not know:

-   who can help;
-   where to find a service;
-   what resources are nearby;
-   which information is authoritative;
-   how to contact the appropriate local institution.

At the same time, other residents may have:

-   skills;
-   tools;
-   spare items;
-   time;
-   local knowledge.

The original concept therefore included mutual aid and skill exchange.

## 5.2 Information Problem

Local information is frequently distributed across unrelated channels.

Example:

``` text
Population data       → Excel
Announcements         → WhatsApp
Facilities            → Google Maps
Services              → Village office
Community information → Individuals
Administrative docs   → Documents
```

This produces:

-   fragmented information;
-   difficult search;
-   inconsistent information;
-   outdated records;
-   manual processes;
-   poor discoverability.

## 5.3 Administrative Problem

A key field discovery is that a Dukuh may already possess a master Excel
dataset supplied by Kelurahan.

Therefore the problem is not necessarily lack of data.

The problem is:

> **Existing data needs a flexible digital interface, workflow,
> access-control layer, and community-service layer around it.**

------------------------------------------------------------------------

# 6. Core Product Principle

## Bring Your Own Data Source (BYODS)

LocalHost should adapt to existing organizational infrastructure.

Supported conceptual sources:

``` text
Excel
CSV
Google Sheets
Google Drive
PostgreSQL
MySQL
Other databases
REST API
Government API
LocalHost database
Other institutional systems
```

The UI and business logic should not depend on one provider.

------------------------------------------------------------------------

# 7. Product Goals

1.  Structure local information.
2.  Connect residents with local administration.
3.  Make local information searchable.
4.  Simplify local service discovery.
5.  Enable controlled community contribution.
6.  Enable administrative verification.
7.  Integrate existing data sources.
8.  Support hierarchical administrative structures.
9.  Support deployments beginning at Dukuh level.
10. Allow later integration with Desa/Kelurahan and Kecamatan.
11. Preserve data ownership and administrative scope.
12. Provide auditable workflows.
13. Create reusable digital infrastructure for multiple communities.

------------------------------------------------------------------------

# 8. Non-Goals

LocalHost is not intended to:

-   replace WhatsApp;
-   replace Instagram;
-   become a generic social network;
-   become a public microblogging platform;
-   replace national identity infrastructure;
-   replace all government systems;
-   expose sensitive population data publicly;
-   become an unrestricted messaging platform;
-   provide professional emergency response itself;
-   require complete data migration;
-   immediately digitize every government service;
-   require nationwide deployment from the beginning.

------------------------------------------------------------------------

# 9. Target Users

## 9.1 Resident

Needs:

-   local information;
-   services;
-   announcements;
-   facilities;
-   community resources;
-   mutual aid;
-   ability to contribute corrections.

## 9.2 RT Administrator

Needs:

-   resident information;
-   verification;
-   local announcements;
-   contribution review;
-   community requests.

## 9.3 RW Administrator

Needs:

-   visibility over multiple RTs;
-   verification;
-   announcements;
-   coordination;
-   statistics.

## 9.4 Dukuh Administrator

Needs:

-   community management;
-   resident information;
-   local resources;
-   services;
-   announcements;
-   contributions;
-   mutual aid.

## 9.5 Desa/Kelurahan Administrator

Needs:

-   population overview;
-   administrative hierarchy;
-   Dukuh/RT/RW management;
-   service directory;
-   verification;
-   data-source management;
-   announcements;
-   statistics;
-   data freshness.

## 9.6 Kecamatan Administrator

Needs:

-   cross-Desa/Kelurahan aggregation;
-   monitoring;
-   coordination;
-   analytics;
-   program-level visibility.

## 9.7 Platform Administrator

Manages:

-   organizations;
-   deployments;
-   integrations;
-   feature flags;
-   security;
-   platform configuration.

------------------------------------------------------------------------

# 10. Administrative Hierarchy

The core model is hierarchical.

``` text
LocalHost Platform
    │
    └── Organization
          │
          └── Administrative Hierarchy
                │
                ├── Kecamatan
                │      ├── Desa
                │      │    └── Dukuh
                │      │         └── RW / RT
                │      │
                │      └── Kelurahan
                │           └── Dukuh
                │
                └── Other configured units
```

Not every deployment requires every level.

------------------------------------------------------------------------

# 11. Platform, Organization, Administrative Unit, Scope

These four concepts should be separate.

## Platform

The entire LocalHost SaaS/platform.

## Organization

The customer or institution responsible for a deployment.

## Administrative Unit

A geographic/administrative unit such as:

-   Kecamatan
-   Desa
-   Kelurahan
-   Dukuh
-   RW
-   RT

## Scope

The part of the administrative hierarchy that a user is authorized to
access or manage.

Example:

``` text
Organization:
Local Government X

Administrative units:
Kecamatan A
 ├── Desa B
 │    ├── Dukuh C
 │    └── Dukuh D
 └── Kelurahan E
```

A user may have:

``` text
scope = Dukuh C
```

while another has:

``` text
scope = Kecamatan A
```

------------------------------------------------------------------------

# 12. Administrative Unit Model

Suggested entity:

``` text
administrative_units
├── id
├── organization_id
├── parent_id
├── name
├── type
├── status
├── configuration
├── created_at
└── updated_at
```

Possible `type` values:

``` text
province
kabupaten
kota
kecamatan
desa
kelurahan
dukuh
rw
rt
```

The model should remain configurable rather than hard-coded to one
locality.

------------------------------------------------------------------------

# 13. Hierarchical Access Control

Conceptually:

``` text
Resident
  ↓
Own data + authorized community information

RT Admin
  ↓
RT scope

RW Admin
  ↓
RW + subordinate RTs

Dukuh Admin
  ↓
Dukuh + subordinate structures

Desa/Kelurahan Admin
  ↓
Desa/Kelurahan scope

Kecamatan Admin
  ↓
Authorized participating Desa/Kelurahan scopes
```

Higher administrative scope does not automatically imply unrestricted
access to sensitive fields.

------------------------------------------------------------------------

# 14. Data Sovereignty

Requirement:

> **Administrative integration must not automatically mean unrestricted
> data access.**

For example:

``` text
Kelurahan
  ├── Population statistics       ✓
  ├── Service information         ✓
  ├── Dukuh information           ✓
  ├── Individual address          restricted
  ├── Phone number                restricted
  ├── Blood type                  restricted
  └── Private administrative data restricted
```

Access depends on:

-   role;
-   scope;
-   data sensitivity;
-   source ownership;
-   configured policy.

------------------------------------------------------------------------

# 15. Deployment Levels

## 15.1 Dukuh Deployment

``` text
Dukuh
├── RW / RT
└── Residents
```

Focus:

-   local information;
-   residents;
-   community;
-   contributions;
-   services;
-   mutual aid.

## 15.2 Desa/Kelurahan Deployment

``` text
Desa/Kelurahan
├── Dukuh A
├── Dukuh B
├── Dukuh C
└── RT/RW
```

Focus:

-   administration;
-   population;
-   services;
-   verification;
-   cross-Dukuh coordination;
-   data sources.

## 15.3 Kecamatan Federation

``` text
Kecamatan
├── Desa A
├── Desa B
├── Kelurahan C
└── ...
```

Focus:

-   aggregation;
-   monitoring;
-   coordination;
-   analytics;
-   cross-unit programs.

Kecamatan should be treated as a federation/coordination layer rather
than simply a larger village application.

------------------------------------------------------------------------

# 16. Bottom-Up Adoption

LocalHost should support:

``` text
Stage 1
Dukuh adopts LocalHost

        ↓

Stage 2
More Dukuhs join

        ↓

Stage 3
Desa/Kelurahan integrates them

        ↓

Stage 4
Kecamatan federates participating units
```

This allows adoption without requiring a complete government-wide
rollout from day one.

------------------------------------------------------------------------

# 17. Dukuh → Kelurahan Integration

Example:

Initial:

``` text
LocalHost
└── Dukuh Ngijon
```

Later:

``` text
LocalHost
└── Kelurahan Sendangarum
     └── Dukuh Ngijon
```

The existing Dukuh data and users should not need to be recreated.

The platform establishes:

``` text
Dukuh Ngijon
parent_id
→ Kelurahan Sendangarum
```

plus:

-   permissions;
-   data-sharing policies;
-   administrative relationship;
-   audit history.

------------------------------------------------------------------------

# 18. Integration Workflow

``` mermaid
flowchart LR
    A["Kelurahan Admin"]
    --> B["Find Dukuh"]

    B --> C["Send Integration Request"]

    C --> D["Dukuh Admin"]

    D --> E{"Confirm?"}

    E -->|Yes| F["Create Parent Relationship"]
    E -->|No| G["Remain Independent"]

    F --> H["Configure Data Sharing"]
    H --> I["Apply Permissions"]
    I --> J["Integrated Platform"]
```

Integration should remain explicit and auditable even if an external
agreement already exists.

------------------------------------------------------------------------

# 19. Integration Without Database Merging

Do not require:

``` text
Dukuh database
+
Kelurahan database
↓
physical database merge
```

Instead:

``` text
Dukuh deployment
        ↓
Administrative relationship
        +
Federated permissions
        +
Data-sharing policy
        +
Logical aggregation
```

Existing data can remain in its original source where appropriate.

------------------------------------------------------------------------

# 20. Data Source Architecture

``` mermaid
flowchart TB

    subgraph SOURCES["Existing Data Sources"]
        A["Excel"]
        B["CSV"]
        C["Google Sheets"]
        D["Google Drive"]
        E["Existing Database"]
        F["REST API"]
        G["Government API"]
        H["LocalHost DB"]
    end

    SOURCES --> I["Data Source Adapter Layer"]
    I --> J["Schema Mapping"]
    J --> K["Validation"]
    K --> L["Canonical LocalHost Data Model"]

    L --> M["Access Control"]
    L --> N["Verification"]
    L --> O["Application Workflows"]

    M --> P["Resident App"]
    N --> Q["Admin Dashboard"]
    O --> R["Community Services"]
```

------------------------------------------------------------------------

# 21. Data Source Modes

## 21.1 Import

``` text
Excel / CSV
 ↓
Upload
 ↓
Schema detection
 ↓
Field mapping
 ↓
Validation
 ↓
Preview
 ↓
Import
```

## 21.2 Synchronization

``` text
External source
 ↓
Scheduled sync
 ↓
Change detection
 ↓
LocalHost read model
```

## 21.3 Live API

``` text
LocalHost
 ↓
External API
 ↓
Source
 ↓
Response
```

## 21.4 Native

``` text
LocalHost
 ↓
Supabase PostgreSQL
```

------------------------------------------------------------------------

# 22. Data Source Priority

## MVP

-   Excel/XLSX
-   CSV
-   LocalHost database

## Phase 2

-   Google Sheets
-   Google Drive

## Phase 3

-   REST API
-   PostgreSQL
-   MySQL
-   other databases

## Phase 4

-   government APIs
-   institutional systems
-   webhooks
-   custom integrations

The architecture should support these from the beginning, but
implementation should be incremental.

------------------------------------------------------------------------

# 23. Data Source Adapter

``` ts
interface DataSourceAdapter {
  connect(): Promise<void>;
  testConnection(): Promise<boolean>;

  getResidents(): Promise<Resident[]>;
  getHouseholds(): Promise<Household[]>;

  getUpdatedSince(date: Date): Promise<unknown[]>;

  getMetadata(): Promise<DataSourceMetadata>;
}
```

Potential adapters:

``` text
ExcelAdapter
CSVAdapter
GoogleSheetsAdapter
GoogleDriveAdapter
PostgresAdapter
MySQLAdapter
RestApiAdapter
GovernmentApiAdapter
LocalDatabaseAdapter
```

Business logic should call the generic adapter rather than a
provider-specific implementation.

------------------------------------------------------------------------

# 24. Schema Mapping

Different organizations may have different field names.

Example:

``` text
NAMA_WARGA
Nama Lengkap
Full Name
nama
```

all map to:

``` text
resident.full_name
```

Likewise:

``` text
No KK
Nomor KK
KK
family_card_number
```

map to:

``` text
household.identifier
```

------------------------------------------------------------------------

# 25. Data Source Metadata

Recommended fields:

``` text
data_sources
├── id
├── organization_id
├── administrative_unit_id
├── name
├── type
├── mode
├── owner
├── authority_level
├── status
├── configuration
├── last_synced_at
└── created_at
```

Record-level metadata:

``` text
source_type
source_reference
source_record_id
source_updated_at
last_synced_at
sync_status
```

------------------------------------------------------------------------

# 26. Data Ownership

Data should be classified as:

## Source-owned

Example:

Official population records supplied by an administrative authority.

## LocalHost-owned

Example:

-   community requests;
-   contributions;
-   announcements;
-   contextual conversations.

## Derived

Example:

-   population statistics;
-   contribution counts;
-   data freshness;
-   aggregated metrics.

This distinction prevents accidental overwriting of authoritative source
data.

------------------------------------------------------------------------

# 27. Conflict Resolution

Example:

``` text
External source:
Muhammad

LocalHost:
Muhammad Fauzan
```

Do not blindly overwrite.

Workflow:

``` text
Conflict detected
      ↓
Review
      ├── Keep source
      ├── Keep LocalHost
      └── Manual resolution
      ↓
Audit log
```

------------------------------------------------------------------------

# 28. Core Modules

1.  Identity & Access
2.  Administrative Hierarchy
3.  Resident Profile
4.  Household & Population
5.  Data Sources
6.  Search
7.  Community Information
8.  Government Services
9.  Facilities
10. Announcements
11. Verification
12. Contribution
13. Mutual Aid
14. Community Directory
15. Forum
16. Contextual Chat
17. Map
18. Notifications
19. Dashboards
20. Analytics
21. Audit & Governance

------------------------------------------------------------------------

# 29. Identity & Access

Features:

-   authentication;
-   registration/invitation;
-   roles;
-   organization membership;
-   administrative scope;
-   permissions;
-   session management.

Roles may include:

``` text
platform_admin
organization_admin
kecamatan_admin
village_admin
dukuh_admin
rw_admin
rt_admin
resident
```

Not every deployment needs all roles.

------------------------------------------------------------------------

# 30. Resident Profile

Possible fields:

-   name;
-   profile image;
-   contact information;
-   household relationship;
-   administrative location;
-   optional skills;
-   optional resources;
-   contribution history.

Sensitive information requires additional authorization.

------------------------------------------------------------------------

# 31. Household & Population

Functions:

-   resident search;
-   household search;
-   filters;
-   RT/RW relationship;
-   verification;
-   correction requests;
-   source tracking;
-   data freshness.

The original project explicitly proposed population search and
blood-type search as features.

------------------------------------------------------------------------

# 32. Blood-Type Search

Blood-type search may remain as a use case, but it must be treated as
sensitive information.

Example:

``` text
Authorized user
      ↓
Blood-type search
      ↓
Permission check
      ↓
Authorized result
```

It must not become unrestricted public search.

------------------------------------------------------------------------

# 33. Search

Global search:

``` text
Residents
Households
Services
Facilities
Announcements
Requests
Community resources
```

Filters:

``` text
RT
RW
Dukuh
Category
Location
Status
Verification
```

------------------------------------------------------------------------

# 34. Community Information

Each administrative unit may have:

-   profile;
-   geography;
-   population summary;
-   administrative structure;
-   facilities;
-   services;
-   contacts;
-   announcements;
-   community programs.

------------------------------------------------------------------------

# 35. Government Service Directory

Service fields:

``` text
Service
├── Name
├── Description
├── Requirements
├── Procedure
├── Responsible Unit
├── Contact
├── Location
├── Operating Hours
└── Status
```

MVP focus:

> Discover and understand services.

Later:

> Submit and track services digitally.

------------------------------------------------------------------------

# 36. Community Directory

## People

-   RT/RW;
-   volunteers;
-   coordinators;
-   verified contributors.

## Places

-   village office;
-   health facilities;
-   community hall;
-   sports facilities;
-   public/community facilities.

## Services

-   technicians;
-   local services;
-   community businesses.

------------------------------------------------------------------------

# 37. Announcements

Announcement sources:

``` text
Kecamatan
Desa/Kelurahan
Dukuh
RW
RT
Community
```

Announcements can target:

-   entire administrative scope;
-   child unit;
-   specific community.

------------------------------------------------------------------------

# 38. Contribution

Residents can:

-   correct their own information;
-   report outdated information;
-   suggest facilities;
-   submit resources;
-   report incorrect information.

Workflow:

``` mermaid
flowchart LR
    A["Resident"]
    --> B["Submit Contribution"]

    B --> C["Review"]

    C --> D{"Valid?"}

    D -->|Yes| E["Approve"]
    D -->|No| F["Reject"]

    E --> G["Update Data"]
    G --> H["Audit Log"]
```

------------------------------------------------------------------------

# 39. Contribution Recognition

The original MVP includes contribution points and contribution levels.

Potential model:

``` text
Contribution
     ↓
Verification
     ↓
Points
     ↓
Recognition level
```

Example recognition levels may be configurable per deployment.

Contribution levels must not:

-   measure human worth;
-   determine access to public services;
-   become an opaque citizen score.

------------------------------------------------------------------------

# 40. Mutual Aid

The original product concept has two primary user states:

### Need help

``` text
Need
 ↓
Create request
 ↓
Nearby residents
 ↓
Receive help
 ↓
Appreciation
```

### Have something to offer

``` text
Have skill/resource
 ↓
See request
 ↓
Offer help
 ↓
Complete
 ↓
Recognition
```

Mutual aid remains an important community module.

------------------------------------------------------------------------

# 41. Mutual Aid Request

Fields:

``` text
title
description
category
location
time
urgency
visibility
status
```

Lifecycle:

``` text
Created
 ↓
Open
 ↓
Response
 ↓
Accepted
 ↓
In Progress
 ↓
Completed
 ↓
Closed
```

------------------------------------------------------------------------

# 42. Matching

Initial matching:

``` text
Category
+
Distance
+
Availability
+
Verification
```

Advanced matching can be introduced later.

------------------------------------------------------------------------

# 43. Trust

Avoid a single opaque citizen score.

Prefer explainable signals:

``` text
✓ Verified Resident

12 Contributions
8 Successful Helps
5 Community Appreciations
```

------------------------------------------------------------------------

# 44. Forum

Features:

-   posts;
-   comments;
-   reporting;
-   moderation.

The forum should remain community-oriented rather than becoming a
general social network.

------------------------------------------------------------------------

# 45. Contextual Chat

LocalHost should not attempt to replace WhatsApp.

Chat should be associated with a context:

``` text
Request
 ↓
Response
 ↓
Contextual Chat
 ↓
Completion
 ↓
Close
```

MVP:

-   1:1 request chat;
-   realtime;
-   unread status;
-   report/block;
-   tied to a request.

Avoid initially:

-   voice/video;
-   stories;
-   complex reactions;
-   unrestricted village-wide messaging.

------------------------------------------------------------------------

# 46. Map

Map may display:

-   facilities;
-   services;
-   public resources;
-   community points;
-   appropriate active requests.

Sensitive residential locations must not be exposed.

------------------------------------------------------------------------

# 47. Dashboards

## Resident

``` text
Home
├── Announcements
├── Services
├── Community
├── Requests
└── Contributions
```

## RT/RW

``` text
Dashboard
├── Residents
├── Verification
├── Contributions
├── Requests
└── Announcements
```

## Dukuh

``` text
Dashboard
├── Residents
├── RT/RW
├── Services
├── Contributions
├── Requests
└── Data Freshness
```

## Desa/Kelurahan

``` text
Dashboard
├── Population
├── Dukuh
├── RT/RW
├── Services
├── Verification
├── Announcements
├── Statistics
└── Data Sources
```

## Kecamatan

``` text
Dashboard
├── Desa/Kelurahan
├── Population Summary
├── Service Statistics
├── Data Freshness
├── Community Programs
├── Cross-Unit Metrics
└── Reports
```

------------------------------------------------------------------------

# 48. Kecamatan Boundary

Kecamatan is a coordination and aggregation layer, not simply a larger
village application.

Primary functions:

-   aggregation;
-   monitoring;
-   coordination;
-   reporting;
-   cross-unit analytics.

Detailed resident data remains subject to authorization.

------------------------------------------------------------------------

# 49. Data Freshness

Administrators should be able to see data freshness.

Example:

``` text
Population
██████████░░ 84% recent

RT 01
✓ Updated

RT 02
⚠ 3 months old

RT 03
✓ Updated
```

This lets administrators identify records that need review.

------------------------------------------------------------------------

# 50. Privacy and Security

Core principles:

-   data minimization;
-   least privilege;
-   explicit visibility;
-   tenant isolation;
-   administrative scope;
-   auditability;
-   sensitive-data controls;
-   database-level enforcement.

------------------------------------------------------------------------

# 51. Security Architecture

``` text
User
 ↓
Authentication
 ↓
Organization Membership
 ↓
Administrative Scope
 ↓
Role
 ↓
Permission
 ↓
Row-Level Security
 ↓
Resource
```

Supabase/PostgreSQL Row Level Security should enforce database
boundaries.

Frontend-only permission checks are insufficient.

------------------------------------------------------------------------

# 52. Audit Log

Every significant administrative action should record:

``` text
actor
action
target
timestamp
scope
source
before
after
```

Examples:

``` text
RT Admin
→ verified resident

Dukuh Admin
→ published announcement

Kelurahan Admin
→ approved correction

System
→ synchronized external source
```

------------------------------------------------------------------------

# 53. Technical Stack

  Layer              Technology
  ------------------ -----------------------------------------------
  Frontend           Next.js
  Language           TypeScript
  UI                 React
  Styling            Tailwind CSS
  Database           PostgreSQL
  Backend platform   Supabase
  Authentication     Supabase Auth
  Storage            Supabase Storage
  Realtime           Supabase Realtime
  Serverless logic   Supabase Edge Functions / server-side Next.js
  Hosting            Vercel
  Source control     GitHub

------------------------------------------------------------------------

# 54. Serverless-First Architecture

Initial infrastructure:

``` text
GitHub
 ↓
Coolify
 ↓
Next.js
 ↓
Supabase
 ├── PostgreSQL
 ├── Auth
 ├── Storage
 ├── Realtime
 └── Edge Functions
```

The platform should avoid requiring:

-   VPS;
-   Kubernetes;
-   manually managed database servers;
-   always-on backend infrastructure.

------------------------------------------------------------------------

# 55. Database Entities

Core:

``` text
organizations

administrative_units
administrative_unit_memberships

users
roles
permissions

households
residents

services
facilities

requests
request_responses

contributions
verifications

announcements

forum_posts
forum_comments

conversations
messages

notifications

data_sources
data_source_mappings
sync_jobs
sync_records

audit_logs
```

------------------------------------------------------------------------

# 56. Scope-Aware Data Model

Relevant entities should reference their administrative scope.

Examples:

``` text
resident
→ administrative_unit_id

request
→ administrative_unit_id

announcement
→ administrative_unit_id

service
→ administrative_unit_id

facility
→ administrative_unit_id
```

This allows policy engines and RLS to determine access.

------------------------------------------------------------------------

# 57. API Domains

Potential domains:

``` text
/api/auth
/api/users
/api/residents
/api/households
/api/administrative-units
/api/services
/api/facilities
/api/requests
/api/contributions
/api/announcements
/api/forum
/api/notifications
/api/data-sources
/api/sync
/api/admin
```

Not every operation requires a custom API. Supabase client access with
RLS can handle ordinary CRUD operations.

Privileged operations should use server-side logic or Edge Functions.

------------------------------------------------------------------------

# 58. Data Synchronization

``` mermaid
flowchart TB
    A["External Source"]
    --> B["Adapter"]

    B --> C["Schema Mapping"]
    C --> D["Validation"]
    D --> E["Change Detection"]

    E --> F{"Changed?"}

    F -->|No| G["No Action"]
    F -->|Yes| H["Sync Record"]

    H --> I["Conflict Check"]

    I --> J{"Conflict?"}

    J -->|No| K["Update Read Model"]
    J -->|Yes| L["Review Queue"]

    L --> M["Admin Resolution"]
    M --> K

    K --> N["Audit Log"]
```

------------------------------------------------------------------------

# 59. Federation Architecture

Kecamatan should not require all child databases to be physically
merged.

Conceptually:

``` text
Kecamatan
    │
    ├── Desa A LocalHost
    ├── Desa B LocalHost
    └── Kelurahan C LocalHost
```

The federation layer provides:

-   identity relationships;
-   authorized aggregation;
-   shared identifiers;
-   data-sharing policies;
-   cross-unit analytics.

------------------------------------------------------------------------

# 60. Feature Flags

Different deployments may enable different capabilities.

Example:

``` json
{
  "mutualAid": true,
  "forum": true,
  "contextualChat": false,
  "populationSearch": true,
  "googleSheets": true,
  "governmentApi": false,
  "map": true
}
```

This prevents the platform from becoming rigid.

------------------------------------------------------------------------

# 61. MVP

## Must Have

### Platform

-   authentication;
-   organization;
-   administrative hierarchy;
-   roles;
-   scope-based permissions.

### Community

-   residents;
-   households;
-   RT/RW;
-   Dukuh.

### Information

-   search;
-   filtering;
-   community information;
-   services;
-   facilities.

### Administration

-   verification;
-   announcements;
-   dashboard;
-   contribution/correction.

### Data

-   Excel import;
-   CSV import;
-   schema mapping;
-   validation;
-   preview;
-   source metadata.

------------------------------------------------------------------------

# 62. MVP Phase 1

``` text
Authentication
      ↓
Administrative Hierarchy
      ↓
Resident Data
      ↓
Search
      ↓
Services
      ↓
Announcements
      ↓
Verification
      ↓
Contribution
```

The purpose is to prove the platform architecture, not to implement
every possible feature.

------------------------------------------------------------------------

# 63. Phase 2

Add:

-   Google Sheets;
-   Google Drive;
-   mutual aid;
-   map;
-   notifications;
-   contribution levels;
-   forum.

------------------------------------------------------------------------

# 64. Phase 3

Add:

-   contextual chat;
-   database connectors;
-   REST API;
-   synchronization engine;
-   advanced conflict resolution.

------------------------------------------------------------------------

# 65. Phase 4

Add:

-   government APIs;
-   administrative submissions;
-   Kecamatan federation;
-   cross-Desa/Kelurahan analytics;
-   institutional integrations.

------------------------------------------------------------------------

# 66. Roadmap

``` mermaid
flowchart LR
    A["Prototype"]
    --> B["Dukuh MVP"]

    B --> C["Desa / Kelurahan"]

    C --> D["Multi-Dukuh"]

    D --> E["Kecamatan Federation"]

    E --> F["Institutional Infrastructure"]
```

------------------------------------------------------------------------

# 67. Adoption Strategy

LocalHost should support bottom-up adoption.

### Stage 1

One Dukuh adopts LocalHost.

### Stage 2

Additional Dukuhs join.

### Stage 3

Desa/Kelurahan integrates participating units.

### Stage 4

Kecamatan federates participating Desa/Kelurahan.

This means the product does not need a massive initial government
contract to demonstrate value.

------------------------------------------------------------------------

# 68. Why Start With Dukuh?

A Dukuh deployment provides:

-   smaller population;
-   smaller administrative scope;
-   easier feedback;
-   easier data validation;
-   shorter decision chain;
-   manageable pilot scope.

It can function as the initial proof of the platform.

------------------------------------------------------------------------

# 69. Why Desa/Kelurahan Is the Main Full Deployment

At Desa/Kelurahan level, LocalHost can combine:

``` text
Population
+
Dukuh
+
RT/RW
+
Services
+
Facilities
+
Announcements
+
Verification
+
Data sources
+
Community
```

This is the natural level for a full administrative deployment.

------------------------------------------------------------------------

# 70. Why Kecamatan Is Different

Kecamatan should focus on:

``` text
Desa/Kelurahan
      ↓
Operational administration

Kecamatan
      ↓
Coordination
Aggregation
Monitoring
Analytics
```

It should not automatically become one huge database containing every
sensitive resident field.

------------------------------------------------------------------------

# 71. Business Model

LocalHost can operate as:

> **B2G / B2B2C SaaS**

Customers:

-   Dukuh/community organizations;
-   Desa;
-   Kelurahan;
-   Kecamatan;
-   other local institutions.

Users:

-   residents;
-   RT/RW;
-   local administrators.

Revenue possibilities:

-   annual subscription;
-   deployment;
-   configuration;
-   training;
-   support;
-   data integration;
-   premium analytics;
-   custom institutional integrations.

------------------------------------------------------------------------

# 72. Pricing Model

Avoid four completely separate products.

Use:

``` text
LocalHost Platform
       │
       ├── Community / Dukuh
       ├── Desa / Kelurahan
       └── Kecamatan
```

Pricing can depend on:

``` text
Administrative scope
+
Population
+
Number of administrative units
+
Data integrations
+
Support level
+
Enabled modules
```

Exact pricing should be established after pilot economics are known.

------------------------------------------------------------------------

# 73. Success Metrics

## Resident

-   search completion rate;
-   service discovery;
-   information retrieval;
-   successful requests.

## Administration

-   verification turnaround;
-   data freshness;
-   correction completion;
-   active administrative units.

## Community

-   contributions;
-   fulfilled requests;
-   successful mutual-aid interactions;
-   community participation.

## Integration

-   synchronization success;
-   synchronization failure rate;
-   source freshness;
-   connected data sources.

------------------------------------------------------------------------

# 74. North Star Metric

> **Successful Local Needs Resolved**

Possible successful resolutions:

``` text
Information found
Service discovered
Request fulfilled
Data correction completed
Administrative information obtained
```

This is more aligned with LocalHost's purpose than DAU alone.

------------------------------------------------------------------------

# 75. Habit Model

The original project uses the Hook Model:

``` text
Trigger
 ↓
Action
 ↓
Variable Reward
 ↓
Investment
 ↓
Repeated Use
```

For LocalHost:

``` mermaid
flowchart LR
    A["Trigger<br/>Local need"]
    --> B["Action<br/>Search / Request"]

    B --> C["Reward<br/>Useful result"]

    C --> D["Investment<br/>Contribute / Verify"]

    D --> E["Better local information"]

    E --> A
```

The intended habit is not simply opening the app. It is using and
improving local information when local needs arise.

------------------------------------------------------------------------

# 76. Product Boundaries

LocalHost owns/provides:

-   identity;
-   administrative hierarchy;
-   community information;
-   services;
-   facilities;
-   search;
-   verification;
-   contributions;
-   mutual aid;
-   announcements;
-   workflows;
-   data integration;
-   access control;
-   audit.

LocalHost does not attempt to own:

-   social media;
-   public microblogging;
-   unrestricted messaging;
-   national identity infrastructure;
-   every government system.

------------------------------------------------------------------------

# 77. Final Architecture

``` mermaid
flowchart TB

    P["LOCALHOST PLATFORM"]

    P --> O["Organizations"]

    O --> H["Administrative Hierarchy"]

    H --> K["Kecamatan"]
    K --> D1["Desa / Kelurahan"]
    D1 --> DU["Dukuh"]
    DU --> RW["RW / RT"]
    RW --> R["Residents"]

    P --> DATA["Data Source Infrastructure"]

    DATA --> E["Excel / CSV"]
    DATA --> GS["Google Sheets"]
    DATA --> GD["Google Drive"]
    DATA --> DB["Existing Database"]
    DATA --> API["REST / Government API"]
    DATA --> LH["LocalHost Database"]

    P --> CORE["Platform Services"]

    CORE --> ID["Identity & Access"]
    CORE --> SR["Search"]
    CORE --> SV["Services"]
    CORE --> CM["Community"]
    CORE --> MA["Mutual Aid"]
    CORE --> CO["Contribution"]
    CORE --> VF["Verification"]
    CORE --> AN["Announcements"]
    CORE --> NT["Notifications"]
    CORE --> AU["Audit"]

    P --> UI["Applications"]

    UI --> RES["Resident"]
    UI --> ADM["Dukuh / RT / RW"]
    UI --> GOV["Desa / Kelurahan"]
    UI --> FED["Kecamatan"]
```

------------------------------------------------------------------------

# 78. Final Product Definition

## Short

> **LocalHost is a multi-tenant community-government digital platform.**

## Technical

> **LocalHost is a hierarchical, source-agnostic digital infrastructure
> for connecting residents, local administrative units, services,
> community workflows, and existing institutional data sources.**

## Architecture

> **LocalHost uses a reusable administrative and data-integration
> framework that allows a deployment to start at Dukuh level, integrate
> into Desa/Kelurahan, and participate in Kecamatan-level federation
> without rebuilding the system.**

## For a Dukuh administrator

> **"Data yang sudah ada tetap bisa digunakan. LocalHost menjadi lapisan
> untuk mengelola, mencari, memverifikasi, dan menggunakan data serta
> layanan warga."**

## For Desa/Kelurahan

> **"LocalHost menghubungkan Dukuh, RT/RW, data, layanan, dan warga
> dalam satu platform tanpa harus memaksa seluruh data existing
> dipindahkan."**

## For Kecamatan

> **"LocalHost menyediakan layer koordinasi dan agregasi
> antar-Desa/Kelurahan tanpa menjadikan Kecamatan sebagai satu database
> raksasa yang membuka seluruh data warga."**

------------------------------------------------------------------------

# 79. Core Architectural Principles

1.  **Platform, not merely an app.**
2.  **Digital infrastructure underneath the platform.**
3.  **Reusable framework behind the architecture.**
4.  **Source-agnostic data integration.**
5.  **Hierarchical administrative model.**
6.  **Scope-based authorization.**
7.  **Data sovereignty.**
8.  **Federation instead of forced database merging.**
9.  **Incremental adoption.**
10. **Modular features.**
11. **Auditable administrative workflows.**
12. **Privacy by design.**
13. **Serverless-first implementation.**
14. **Start small, expand upward.**
15. **Do not force institutions to abandon existing systems.**
16. **Coolify-first, container-friendly deployment.**

------------------------------------------------------------------------

# 80. One-Sentence Pitch

> **LocalHost is a community-government digital platform that connects
> residents, local administration, services, and existing institutional
> data through a hierarchical, source-agnostic infrastructure that can
> start from a Dukuh and scale to Desa/Kelurahan and Kecamatan.**
