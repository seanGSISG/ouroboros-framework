# Command: ouroboros-update

Refresh Ouroboros managed blocks in project CLAUDE.md file.

## Description

This command updates the managed Ouroboros instruction block in your project's root CLAUDE.md file while preserving all user content. The managed block is wrapped in `<!-- OUROBOROS:START -->` and `<!-- OUROBOROS:END -->` markers.

**Use this command when**:
- You've upgraded the Ouroboros framework
- Instructions in the managed block are outdated
- You want to pull the latest spec workflow guidance

## Usage

```
/ouroboros-update
```

## What It Does

1. Locates `{PROJECT_ROOT}/CLAUDE.md`
2. Finds the managed block (<!-- OUROBOROS:START --> ... <!-- OUROBOROS:END -->)
3. Replaces ONLY the content within the markers
4. Preserves ALL user content outside the managed block
5. Reports what was updated

## Example

**Before** (CLAUDE.md):
```markdown
<!-- OUROBOROS:START -->
# Ouroboros Instructions (Old Version)
...old instructions...
<!-- OUROBOROS:END -->

# My Custom Project Instructions
...user content preserved...
```

**After** running `/ouroboros-update`:
```markdown
<!-- OUROBOROS:START -->
# Ouroboros Instructions

These instructions are for AI assistants working in this project.

Always open @/ouroboros/CLAUDE.md when the request:
- Mentions planning or proposals (words like proposal, spec, change, plan)
- Introduces new capabilities, breaking changes, architecture shifts, or big performance/security work
- Sounds ambiguous and you need the authoritative spec before coding

Use @/ouroboros/CLAUDE.md to learn:
- How to create and apply change proposals
- Spec format and conventions
- Project structure and guidelines

Keep this managed block so 'ouroboros update' can refresh the instructions.

<!-- OUROBOROS:END -->

# My Custom Project Instructions
...user content preserved...
```

## Safety

- ✅ Only updates content between markers
- ✅ Never modifies user content
- ✅ Creates backup before updating (CLAUDE.md.backup)
- ✅ Reports if no managed block found
- ✅ Safe to run multiple times (idempotent)

## Implementation

This command executes the following logic:

```typescript
async function updateOuroborosManagedBlocks(projectRoot: string) {
  const claudeMdPath = path.join(projectRoot, 'CLAUDE.md');

  // Check if CLAUDE.md exists
  if (!fs.existsSync(claudeMdPath)) {
    console.log('❌ No CLAUDE.md found in project root');
    console.log('💡 Tip: Run a spec workflow first to auto-create CLAUDE.md');
    return;
  }

  const content = fs.readFileSync(claudeMdPath, 'utf-8');
  const managedBlockRegex = /<!-- OUROBOROS:START -->[\s\S]*?<!-- OUROBOROS:END -->/g;

  // Check if managed block exists
  if (!managedBlockRegex.test(content)) {
    console.log('⚠️  No Ouroboros managed block found in CLAUDE.md');
    console.log('💡 Tip: Add the managed block manually or run a spec workflow');
    return;
  }

  // Get latest managed block content
  const latestBlock = getLatestOuroborosManagedBlock();

  // Create backup
  fs.writeFileSync(claudeMdPath + '.backup', content);

  // Replace managed block
  const updatedContent = content.replace(managedBlockRegex, latestBlock);

  // Write updated file
  fs.writeFileSync(claudeMdPath, updatedContent);

  console.log('✅ Updated Ouroboros managed block in CLAUDE.md');
  console.log('📁 Backup saved: CLAUDE.md.backup');
  console.log('🐍 The serpent refreshes its ancient wisdom...');
}

function getLatestOuroborosManagedBlock(): string {
  return `<!-- OUROBOROS:START -->
# Ouroboros Instructions

These instructions are for AI assistants working in this project.

Always open @/ouroboros/CLAUDE.md when the request:
- Mentions planning or proposals (words like proposal, spec, change, plan)
- Introduces new capabilities, breaking changes, architecture shifts, or big performance/security work
- Sounds ambiguous and you need the authoritative spec before coding

Use @/ouroboros/CLAUDE.md to learn:
- How to create and apply change proposals
- Spec format and conventions
- Project structure and guidelines

Keep this managed block so 'ouroboros update' can refresh the instructions.

<!-- OUROBOROS:END -->`;
}
```

## Output

```
✅ Updated Ouroboros managed block in CLAUDE.md
📁 Backup saved: CLAUDE.md.backup
🐍 The serpent refreshes its ancient wisdom...
```

## Troubleshooting

**Error: No CLAUDE.md found**
- Run a spec workflow first to auto-create CLAUDE.md
- Or create CLAUDE.md manually and add managed block markers

**Error: No managed block found**
- Add the markers manually:
  ```markdown
  <!-- OUROBOROS:START -->
  (content here will be replaced)
  <!-- OUROBOROS:END -->
  ```
- Or run a spec workflow to auto-add the block

**Backup file growing large**
- Safe to delete old .backup files after verifying updates

---

*The serpent renews itself, shedding old scales for new...* 🐍
