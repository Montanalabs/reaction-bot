#! Reaction bot — untrusted a message can only ever become one of a fixed set of decisions over a
#! closed type, never a tool argument. An injected instruction cannot be represented in the
#! closed type, so it is rejected at the trust boundary (and re-clamped at run time by extract).
#! @requires react — the reaction bot sink
#! @effect io
#! @taint bridge — extract<Decision> turns the tainted input into a trusted decision
grant react

type Emoji = ThumbUp | ThumbDown | Heart
type Decision = React(Emoji) | Ignore

let raw = fetch<web>  # UNTRUSTED a message — tainted
quarantined { let d = extract<Decision>(raw) }  # only a fixed Decision (payloads too) crosses
privileged { react(d) }  # act on the trusted decision only
