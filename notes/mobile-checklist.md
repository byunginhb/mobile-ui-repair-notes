# A focused mobile verification checklist

Use this for a small agreed change, not as a reason to test every feature of an application.

## Before a change

Record the public page, viewport, reproduction steps, expected behavior and current revision. Agree which one or two problems belong to the job. Do not test authentication, checkout or customer data without a separate explicit scope.

## After a change

1. Reproduce the original problem at the reported width and confirm its resolution.
2. Check one normal desktop width for a direct layout regression.
3. Follow the changed control by keyboard and verify its visible focus.
4. Check the directly affected interaction and run relevant project checks.
5. Record what was checked and what was not. A preview build, PR merge and production deployment are separate events.

For animation changes, respect the visitor's reduced-motion preference. For screenshots, use synthetic or explicitly permitted data only. If a check fails twice without new evidence, stop repeating it and reassess the cause.
