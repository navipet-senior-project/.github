<div align="center">
  <img src="https://raw.githubusercontent.com/navipet-senior-project/NaviPetFlutter/main/assets/mascot.png" alt="NaviPet mascot" width="180" />

  # NaviPet

  **A student-built campus-navigation companion for California State University, Long Beach.**

  NaviPet combines walking navigation, class planning, task tracking, and a friendly virtual pet in one mobile experience.

  [Mobile app](https://github.com/navipet-senior-project/NaviPetFlutter) · [Backend API](https://github.com/navipet-senior-project/NavipetBackend) · [Product roadmap](https://github.com/orgs/navipet-senior-project/projects/7)
</div>

## About the project

NaviPet is a CSULB senior project that helps students navigate campus and find their destinations without the usual confusion. The mobile app brings together location-aware navigation and everyday academic tools, while the backend supplies a secure foundation for authenticated data and future services.

The current project includes:

- Email/password authentication, password recovery, guest access, and persistent sessions
- A native Mapbox map with live device location
- Destination search, walking routes, ETA and distance previews
- Maneuver guidance, spoken instructions, arrival detection, and rerouting
- Class schedules, generated tasks, daily completion tracking, and account profiles
- Row Level Security for user-owned application data
- OpenAPI documentation and health checks for backend development

## Repositories

| Repository | Responsibility | Main technologies |
| --- | --- | --- |
| [**NaviPetFlutter**](https://github.com/navipet-senior-project/NaviPetFlutter) | Cross-platform NaviPet mobile application for Android and iOS | Flutter, Dart, Mapbox, Supabase |
| [**NavipetBackend**](https://github.com/navipet-senior-project/NavipetBackend) | API, authentication boundary, application services, email delivery, and database schema | TypeScript, Fastify, Render, Supabase, PostgreSQL, Resend |

## Architecture

```mermaid
flowchart LR
    User[Student] --> Mobile[NaviPet Flutter app]
    Mobile --> Mapbox[Mapbox services]
    Mobile --> Auth[Supabase Auth]
    Mobile --> API[Fastify API on Render]
    API --> Auth
    API --> Data[(Supabase PostgreSQL)]
    API --> Email[Resend email service]
```

The Flutter application owns the user experience and on-device navigation flow. Supabase Auth manages identity. The Fastify service runs on Render, validates access tokens, and provides a trusted server boundary for application rules and protected data access. PostgreSQL policies keep profiles, classes, and task progress scoped to their owners. Resend handles transactional email delivery.

## Technology

![Flutter](https://img.shields.io/badge/Flutter-02569B?logo=flutter&logoColor=white)
![Dart](https://img.shields.io/badge/Dart-0175C2?logo=dart&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white)
![Fastify](https://img.shields.io/badge/Fastify-000000?logo=fastify&logoColor=white)
![Render](https://img.shields.io/badge/Render-000000?logo=render&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?logo=supabase&logoColor=white)
![Resend](https://img.shields.io/badge/Resend-000000?logo=resend&logoColor=white)
![Mapbox](https://img.shields.io/badge/Mapbox-000000?logo=mapbox&logoColor=white)
![Unity](https://img.shields.io/badge/Unity-000000?logo=unity&logoColor=white)

Indoor navigation for the Vivian Engineering Center (VEC) is being built with Unity, AR Foundation and MultiSet.

## Start developing

- Follow the [mobile setup guide](https://github.com/navipet-senior-project/NaviPetFlutter#prerequisites) to configure Flutter, Mapbox, and Supabase.
- Follow the [backend setup guide](https://github.com/navipet-senior-project/NavipetBackend#local-api-testing-with-swagger-ui) to run the API and Swagger UI locally.
- Review each repository's environment example before starting. Never commit API secrets or a Supabase service-role key.

## Product roadmap

All work is tracked on the [**NaviPet Product Roadmap**](https://github.com/orgs/navipet-senior-project/projects/7) board. The columns are Product Backlog → Sprint Backlog → In Progress → In Review / PR → Done. Each story has a sprint, epic, priority, Fibonacci story points and Gherkin acceptance criteria.

| Sprint | Goal | Milestone |
| --- | --- | --- |
| 1 | Foundation & authentication: repos, CI/CD, Supabase, registration, login, password reset, VEC scan merged in Unity | [Sprint 1](https://github.com/navipet-senior-project/.github/milestone/1) |
| 2 | Profile, class schedule, destination search, outdoor route preview, VEC floor-1 waypoints | [Sprint 2](https://github.com/navipet-senior-project/.github/milestone/2) |
| 3 *(proposed)* | VEC indoor AR vertical slice: search VEC 404 → route to entrance → launch AR → localize → arrive | [Sprint 3](https://github.com/navipet-senior-project/.github/milestone/3) |
| 4 *(proposed)* | Campus-wide search, place cards, accessible routes, more VEC rooms, pilot test, release candidate | [Sprint 4](https://github.com/navipet-senior-project/.github/milestone/4) |

## Development workflow

1. Pick an issue from the **Sprint Backlog** column, assign yourself and move it to **In Progress**.
2. Create a branch from `main`: `feature/<issue-number>-short-name` or `fix/<issue-number>-short-name`.
3. Commit using [Conventional Commits](https://www.conventionalcommits.org/) (`feat:`, `fix:`, `docs:`, `chore:`).
4. Open a pull request to `main` that references the story (`Refs navipet-senior-project/.github#<n>`) and move the card to **In Review / PR**.
5. `main` is protected in both code repositories: changes land through pull requests. In NavipetBackend, the Lint, Type check, Tests, Build and Security audit checks must pass.
6. After merge, attach demo evidence to the story and move it to **Done** once every item in its Definition of Done is checked.

## Contributing

- Never commit secrets: `.env`, Supabase service-role keys, Mapbox secret tokens or MultiSet credentials. Use each repository's `.env.example`.
- Keep pull requests small and focused on one story or subtask.
- Update the README, Swagger docs or migrations whenever behaviour, API contracts or the database change.
- Report bugs as issues with the `bug` label, steps to reproduce, and the device and OS version.

## Testing

| Repository | Commands |
| --- | --- |
| NaviPetFlutter | `dart format --output=none --set-exit-if-changed .` · `flutter analyze` · `flutter test` · `flutter build apk --debug` |
| NavipetBackend | `npm run lint` · `npm run typecheck` · `npm test` · `npm run build` |

Both repositories run these checks in GitHub Actions on every pull request to `main`. Features that need AR hardware are verified on a physical Android device and recorded in the story.

## Senior project team

NaviPet is developed as a California State University, Long Beach senior project by:

| Team member | Role |
| --- | --- |
| [Khoi Do (@Ben2104)](https://github.com/Ben2104) | Full Stack Lead Developer / Project Manager |
| [Jomar Hernandez (@thejomar)](https://github.com/thejomar) | UI/UX Designer / Mobile Developer | Unity Developer
| [Will Chhuor (@will-chhuor)](https://github.com/will-chhuor) | Mobile Developer |
| [Jake Nomoto (@GlazedKrispy)](https://github.com/GlazedKrispy) | Backend Developer |
| [Jan Montemayor (@Kura-Yami)](https://github.com/Kura-Yami) | Full Stack Developer |

Project work, decisions and progress are tracked on the [product roadmap](https://github.com/orgs/navipet-senior-project/projects/7) and in the two public repositories above.

---

<div align="center">
  Built at CSULB to help students navigate campus and their day.
</div>
