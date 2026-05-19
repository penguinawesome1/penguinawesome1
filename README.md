```rs
let me = Me {
    name: hash("owen"),
    interests: ["rust", "gamedev", "stenography", "najdorf"].map(hash),
    _padding: [0; 3],
};
```

```wgsl
@group(0) @binding(0) var<uniform> me: Me;

@compute @workgroup_size(64)
fn main(@builtin(global_invocation_id) id: vec3u) {
    let passion = me.interests[id.x % 4u];
}
```
