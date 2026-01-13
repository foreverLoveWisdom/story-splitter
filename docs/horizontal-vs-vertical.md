# Horizontal vs Vertical Breakdown

## The One Thing

**Vertical slicing is preferable** - users see value faster - but horizontal is pragmatic when team constraints require it.

## Two Approaches

**Vertical (Preferred)**:

- Each story delivers end-to-end value (backend + frontend + integration)
- User can actually use the feature immediately
- Example: "Story 1: Login with email (complete flow)"

**Horizontal (Pragmatic)**:

- Stories split by technical layer (backend → frontend → integration)
- User waits until all stories complete
- Example: "Story 1: Login API, Story 2: Login UI, Story 3: Wire them together"

## Trade-offs

**Vertical**:

- ✅ Users see value immediately
- ✅ Feedback comes early
- ✅ Can ship partial features
- ❌ Harder for teams (backend + frontend skills needed per story)
- ❌ Requires cross-functional collaboration

**Horizontal**:

- ✅ Easier for specialized teams (backend team, frontend team)
- ✅ Less coordination overhead
- ✅ Team members work in comfort zone
- ❌ Users wait longer for value
- ❌ Integration risks discovered late
- ❌ Can't ship until all layers complete

## When to Use Which

**Use Vertical when**:

- Team is cross-functional (engineers can do backend + frontend)
- Early user feedback is critical
- You want to ship incrementally

**Use Horizontal when**:

- Team is strictly specialized (separate backend/frontend teams)
- High coordination cost between teams
- Current process doesn't support cross-functional work
- **Pragmatic constraint**: It's what your team can do today

## Pragmatic Reality

Sometimes horizontal is necessary due to:

- Organizational structure (separate teams)
- Skill gaps (backend engineers can't write frontend)
- Legacy processes

**Strategy**: Start horizontal if needed, **plan to improve toward vertical** as team matures.

## AI Collaboration Context

Story breakdown prompt asks your preference - answer honestly based on current team constraints, not ideal state. AI will generate appropriate breakdown.

## Learn More

**[Vertical Slices (Richard Lawrence) →](https://agileforall.com/vertical-slices-and-scale/)**
**[Story Splitting Patterns→](https://nextagile.ai/blogs/agile/vertical-slicing-and-horizontal-slicing/)**
