# Milestone 1 (Python + OOP) — Week 1 Daily Plan

Budget: ~14.5 ghonta (12-15). Pace: Implement -> Explain -> Break -> Defend, protita feature-e.
Rule: tumi code likhbe, ami shudhu hint dibo, tarpor review korbo.

Week 1 focus: domain model (Course, Lesson, Student, Enrollment), types, collections, functions, modules, exceptions, pytest, Big-O, list/dict/set.
Week 2-te jabe: generators, decorators, context managers, SOLID, Strategy, Factory, stack/queue, search/sort, 10+ test package finalize.

---

## Day 1 — Setup + Course/Lesson (2h)

| Time | Kaj |
|------|-----|
| 30m | Python 3.12+, venv, pytest install, `pyproject.toml`. (Laravel analogy: venv = vendor/, pyproject = composer.json) |
| 30m | Big-O intro: O(1), O(n), O(n^2), O(log n). Nijer bhasay explain koro, notebook-e lekho |
| 60m | **TASK 1 (tumi nije):** `Course` ar `Lesson` class |

**Task 1 hints (code dibo na):**
- `@dataclass` use koro. Eloquent model-er moto attribute thakbe, kintu DB charai
- `Lesson`: id, title, duration_seconds, order
- `Course`: id, title, price, lessons (list)
- Business rule: duration negative hobe na, title khali hobe na, lesson order unique hobe
- Validation kothay hobe? `__post_init__` vs method. Trade-off chinta koro
- Type hints shob jaygay. `list[Lesson]`, `int`, `str`
- Mutable default (`lessons=[]`) dataclass-e keno bhul? `field(default_factory=list)` kon problem solve kore? Eta tumi explain korbe

**Exit check:** ami review korar age nijeke jiggesh koro: `Course` er lessons list-e duplicate order dhukle ki hoy?

---

## Day 2 — Student + Enrollment + exceptions (2h)

| Time | Kaj |
|------|-----|
| 30m | Concept: custom exception hierarchy (Laravel: domain exception / ValidationException) |
| 90m | `Student`, `Enrollment` class + rules |

**Rules (tumi implement korbe):**
- Ek student ek course-e duibar enroll korte parbe na
- Unpublished course-e enroll kora jabe na
- Enrollment-e progress (completed lesson ids) track hobe
- Progress percentage derive hobe, store hobe na (keno? defend koro)

**Hints:**
- Base `EduStreamError`, tar niche `AlreadyEnrolledError`, `CourseNotPublishedError`
- Enrollment kothay thakbe: Student-er bhitore na alada service? Duita option-er trade-off likho
- `ValueError` vs custom exception kokhon?

---

## Day 3 — Collections + Big-O of own code (2h)

| Time | Kaj |
|------|-----|
| 45m | list, tuple, dict, set: mutable vs immutable, shallow vs deep copy |
| 45m | Tomar Day 2 code-e "student already enrolled?" check: list scan na set/dict? Big-O likho |
| 30m | DSA tracker: Arrays/lists/strings, Hash maps/sets -> **Explain** step |

**Task:** `EnrollmentRegistry` banao jeta `(student_id, course_id)` fast lookup kore.
**Hints:** O(n) list scan vs O(1) average set/dict. 10x, 100x scale-e ki hoy? Hash collision kothay lage, short-e bhabo.

---

## Day 4 — pytest + package structure (2h)

| Time | Kaj |
|------|-----|
| 30m | src layout, `__init__.py`, absolute import, circular import problem |
| 90m | Minimum 10 test (Week 2-er deliverable-er shuru) |

**Test checklist (roadmap theke):** empty input, duplicate, invalid input, edge case.
**Hints:**
- `pytest.raises(AlreadyEnrolledError)`
- `pytest.fixture` diye ekta published course banao (Laravel analogy: factory/setUp)
- Test naam e behavior lekho: `test_cannot_enroll_twice`
- Pehle test fail dekho, tarpor pass koro

---

## Day 5 — Functions + refactor + problems (2h)

| Time | Kaj |
|------|-----|
| 40m | `*args`, `**kwargs`, default args, keyword-only, comprehension, pure function |
| 40m | Nijer code refactor: duplicate kome ana, naming, type hints complete |
| 40m | DSA: Arrays/strings **2 ta problem** (e.g. two-sum, valid anagram) |

---

## Day 6 — Break + Defend (3h, weekend, boro session)

| Time | Kaj |
|------|-----|
| 60m | **Break:** nijer code bhangar try koro. `None`, empty string, huge list, same object twice, negative price |
| 60m | Hash map/set mastery checklist: scratch implementation (simple hash table with chaining) + tests + Big-O |
| 60m | Hash map/set: **3 ta problem** (group anagrams, longest consecutive, subarray sum) |

---

## Day 7 — Review + quiz + progress (1.5h)

| Time | Kaj |
|------|-----|
| 30m | Code review session amar shathe (Task 1 theke Day 5 porjonto) |
| 30m | Interview quiz: mutable vs immutable, shallow vs deep copy, set vs list, Big-O of dict lookup |
| 30m | PROGRESS.md update, git commit, Week 2 plan |

---

## Weekly hour summary

| Day | Ghonta |
|-----|--------|
| 1 | 2 |
| 2 | 2 |
| 3 | 2 |
| 4 | 2 |
| 5 | 2 |
| 6 | 3 |
| 7 | 1.5 |
| **Total** | **14.5** |

## Git repo structure (A to Z)

```
edustream-ai/
├── README.md
├── PROGRESS.md
├── .gitignore
├── docs/
│   ├── adr/            # architecture decision records
│   ├── weekly/         # week-wise plan ar notes (WEEK1_PLAN.md ekhane)
│   └── interview/      # weak areas, quiz log
├── dsa-notebook/       # implementation, tests, complexity notes, problems
├── milestone-1-python-oop/
│   ├── pyproject.toml
│   ├── src/edustream/
│   └── tests/
└── (porer milestone gula pore: django-drf/, fastapi-services/, ...)
```

Commit convention: `m1: add Course and Lesson dataclasses`, `m1: tests for enrollment rules`. Protita task-er por chhoto commit.

## PROGRESS.md-er jonno update (ei session)

- Done: Roadmap review, Week 1 plan, repo structure decision
- In progress: Task 1 (Course + Lesson), tumi korcho
- Next task: Day 1 Task 1, tarpor amake dekhao
- Session log: 2026-10-02: Week 1 daily plan toiri, git repo setup shuru