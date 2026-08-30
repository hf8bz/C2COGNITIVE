# C2Cognitive Application Lanes Guide

**C2Cognitive v1.0.0  |  Release 1  |  30 August 2026**

## Purpose

The Core router is project-agnostic, but C2Cognitive ships domain scopes for recurring engineering lanes. These
scopes are examples/templates to be adopted against real project authority where marked as such; the payments scope
is intentionally stricter.

## Ten non-template scopes

| Scope file | Shipped scope | Activation / authority summary |
| --- | --- | --- |
| [`backend-api.md`](.agent/scopes/backend-api.md) | Scope: Backend / API | Endpoints, services, authentication, authorization, background jobs, third-party integrations. |
| [`data-schema.md`](.agent/scopes/data-schema.md) | Scope: Data and Schema | Tables, columns, indexes, relations, migrations, seeds, heavy queries. |
| [`frontend-web.md`](.agent/scopes/frontend-web.md) | Scope: Frontend Web | Pages, components, client routing, client state, styling, assets. |
| [`infra-deploy.md`](.agent/scopes/infra-deploy.md) | Scope: Infra and Deploy | Environments, secrets, DNS, CDN, pipelines, runtime configuration, deploys. |
| [`mobile-android.md`](.agent/scopes/mobile-android.md) | Scope: Android | Any work touching Android sources, Gradle configuration, Android resources, Play Console metadata, or the Android half of a cross-platform project: `{{ANDROID_MODULE}}`, `**/*.kt`, `**/*.java`, `**/build.gradle*`, `**/AndroidManifest.xml`, `**/res/**`, `**/proguard*.pro`, `gradle/**`, `**/*.aab`, `**/*.apk`. |
| [`mobile-ios.md`](.agent/scopes/mobile-ios.md) | Scope: iOS | Any work touching iOS sources, Xcode project configuration, asset catalogs, entitlements, App Store Connect metadata, or the iOS half of a cross-platform project: `{{IOS_SCHEME}}`, `**/*.swift`, `**/*.m`, `**/*.mm`, `**/*.xcodeproj/**`, `**/*.xcworkspace/**`, `**/*.plist`, `**/*.entitlements`, `**/*.xcassets/**`, `Podfile*`, `Package.swift`, `fastlane/**`. |
| [`mobile-native.md`](.agent/scopes/mobile-native.md) | Scope: Mobile / Native (shared, cross-platform) | Mobile work that is **not** specific to one platform: shared business logic, cross-platform framework code, permission design, offline behaviour, and any decision that has to hold on Android and iOS at the same time. |
| [`payments-sensitive.md`](.agent/scopes/payments-sensitive.md) | Scope: Money and Sensitive Data | The highest-standard scope in this repo. If you are in doubt inside this scope, **stop**. |
| [`qa-tooling.md`](.agent/scopes/qa-tooling.md) | Scope: QA and Tooling | Tests, QA harnesses, browser automation, tool integration, CI. |
| [`ui-ux.md`](.agent/scopes/ui-ux.md) | Scope: UI/UX and Branding | Visual decisions, typography, color, spacing, icons, product naming, copy tone. |

## Backend and API

The backend lane covers endpoint/service/auth changes. It is expected to combine with data-schema, sensitive-data,
infra/deploy, or QA scopes when the work crosses those boundaries rather than letting one generic backend rule set
silently own every concern.

## Data/schema

Schema changes are isolated to migrations. Runtime code, test helpers, fixtures, seeds, and ad-hoc scripts are not a
substitute for an explicit migration path. Rollback/backfill semantics remain part of the change plan.

## Frontend and UI/UX

Frontend behavior and UI/branding are separated so application-state/runtime concerns do not silently become brand
or design authority. Visual changes require real-environment verification; shared design-token changes are treated
as wider-impact changes.

## Infrastructure and deploy

Deploy/environment/DNS/secret work is sensitive. Post-deploy QA is a separate runbook because "deployment command
returned success" is not sufficient evidence that the user-facing system is healthy.

## QA and tooling

Tool availability limits claim strength. Flaky tests are not retried into a selected pass, and a bug-fix test should
demonstrate the failing condition before the fix where practicable.

## Payments and sensitive data

The payments scope is the highest-standard shipped scope. Money-flow changes require explicit human confirmation;
fixed precision, idempotency, state transitions, callback verification, sensitive-log prohibition, audit trail, and
failure-path testing are hard rules in that scope.

## Mobile

Mobile has shared plus Android- and iOS-specific scopes. Build/release, device QA, and store submission are separate
runbooks because a distributed binary cannot be recalled like a replaceable server deploy. Store/legal/privacy
submission declarations remain human decisions.

## Related procedure layer

Application scopes are combined with the relevant runbooks such as database migration, UI audit, post-deploy QA,
browser-tooling recovery, mobile build/release, device QA, store submission, evidence contract, and incident
rollback. The route determines which layers apply.

See [Control Plane Catalog](C2COGNITIVE-CONTROL-PLANE-CATALOG.md) and
[Runbook Catalog](C2COGNITIVE-RUNBOOK-CATALOG.md).
