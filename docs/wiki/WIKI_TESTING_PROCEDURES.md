# 🧪 Wiki System Testing Procedures

**Target Audience**: HaldisB2B team members  
**Prerequisites**: GitHub account with HaldisB2B organization access  
**Testing Duration**: 15-20 minutes per team member  
**Success Criteria**: 100% automated wiki synchronization validation

---

## 📋 Pre-Test Setup Verification

### **Step 1: Access Verification**
```bash
# Verify you have access to the foundation repository
gh repo view HaldisB2B/.github

# Expected output: Repository details with no permission errors
```

### **Step 2: Local Environment Setup**
```bash
# Clone the foundation repository if not already done
git clone https://github.com/HaldisB2B/.github.git
cd .github

# Verify you're on the main branch
git branch --show-current
# Expected output: main

# Check current wiki structure
ls docs/wiki/
# Expected output: Multiple .md files including Home.md, HALDIS_AUTOMATION_STRATEGY.md
```

---

## 🔬 Test Case 1: Basic Wiki Update (Required)

### **Objective**: Verify basic wiki synchronization works correctly

### **Execution Steps**:

**Step 1.1**: Create a test documentation file
```bash
# Create a simple test file
cat > docs/wiki/TEST_WIKI_SYNC.md << 'EOF'
# Test Wiki Synchronization

**Test Created By**: [Your Name]  
**Test Date**: [Current Date]  
**Test Purpose**: Validate automated wiki publishing workflow

## Test Content

This is a test file to verify that:
- ✅ New .md files in docs/wiki/ are automatically published
- ✅ GitHub Actions workflow triggers correctly
- ✅ Wiki content updates in real-time
- ✅ No manual intervention required

## Success Criteria

If you can see this content in the HaldisB2B/.github wiki after pushing this change, the automation is working correctly.

---
*Test file - safe to delete after validation*
EOF
```

**Step 1.2**: Commit and push the test file
```bash
# Add the test file
git add docs/wiki/TEST_WIKI_SYNC.md

# Commit with proper format
git commit -m "test: Add wiki synchronization validation test

Testing automated wiki publishing workflow for team member validation.

🤖 Generated with [Claude Code](https://claude.ai/code)

Co-Authored-By: [Your Name] <your-email@example.com>"

# Push to trigger automation
git push origin main
```

**Step 1.3**: Monitor workflow execution
```bash
# Check if workflow started (wait 30 seconds first)
sleep 30
gh run list --repo HaldisB2B/.github --limit 3

# Expected output: Recent "Publish Haldis DevOps/SysOps Knowledge Base" workflow
```

**Step 1.4**: Verify workflow completion
```bash
# Get the latest run ID
LATEST_RUN=$(gh run list --repo HaldisB2B/.github --limit 1 --json databaseId --jq '.[0].databaseId')

# Check workflow status
gh run view $LATEST_RUN --repo HaldisB2B/.github

# Expected output: Status should show "completed" and "success"
```

### **Success Criteria**:
- ✅ GitHub Actions workflow triggers automatically
- ✅ Workflow completes successfully (status: success)
- ✅ No errors in workflow logs
- ✅ Test file appears in internal wiki (verify with team lead)

---

## 🔬 Test Case 2: Content Update Verification (Required)

### **Objective**: Verify existing content updates propagate correctly

### **Execution Steps**:

**Step 2.1**: Update the test file with additional content
```bash
# Append to the existing test file
cat >> docs/wiki/TEST_WIKI_SYNC.md << 'EOF'

## Update Test

**Update Time**: [Current Time]
**Update By**: [Your Name]

This section was added to test content updates:
- Content modification detection works
- Incremental updates are processed correctly
- No content loss during updates
- Version history is maintained

### Technical Validation

Testing update propagation for:
1. **Existing file modification**: ✅
2. **Content preservation**: ✅
3. **Automated processing**: ✅
4. **Real-time synchronization**: ✅
EOF
```

**Step 2.2**: Commit and push the update
```bash
# Add the updated file
git add docs/wiki/TEST_WIKI_SYNC.md

# Commit the update
git commit -m "test: Update wiki sync test with additional validation content

Testing incremental content updates and modification detection.

🤖 Generated with [Claude Code](https://claude.ai/code)

Co-Authored-By: [Your Name] <your-email@example.com>"

# Push the update
git push origin main
```

**Step 2.3**: Verify update processing
```bash
# Wait for workflow to trigger
sleep 30

# Check latest workflow
gh run list --repo HaldisB2B/.github --limit 2

# Verify both workflows completed successfully
```

### **Success Criteria**:
- ✅ Update triggers new workflow run
- ✅ Workflow processes content changes correctly
- ✅ No existing content is lost or corrupted
- ✅ Updated content appears in wiki

---

## 🔬 Test Case 3: Multiple File Operations (Advanced)

### **Objective**: Test complex operations with multiple files

### **Execution Steps**:

**Step 3.1**: Create multiple test files simultaneously
```bash
# Create a second test file
cat > docs/wiki/MULTI_FILE_TEST_A.md << 'EOF'
# Multi-File Test A

**Created By**: [Your Name]
**Purpose**: Testing multi-file wiki synchronization

This file tests:
- Multiple file creation in single commit
- Batch processing capabilities
- Cross-file link validation
- Simultaneous content publishing

## Cross-Reference Test

See also: [Multi-File Test B](MULTI_FILE_TEST_B)
EOF

# Create a third test file
cat > docs/wiki/MULTI_FILE_TEST_B.md << 'EOF'
# Multi-File Test B

**Created By**: [Your Name]
**Purpose**: Testing batch wiki operations

This file validates:
- Concurrent file processing
- Link relationship maintenance
- Content organization preservation
- Automated cross-referencing

## Cross-Reference Test

See also: [Multi-File Test A](MULTI_FILE_TEST_A)
EOF
```

**Step 3.2**: Commit all files together
```bash
# Add all test files
git add docs/wiki/MULTI_FILE_TEST_*.md

# Commit batch operation
git commit -m "test: Add multi-file wiki synchronization test

Testing batch processing of multiple wiki files with cross-references.

🤖 Generated with [Claude Code](https://claude.ai/code)

Co-Authored-By: [Your Name] <your-email@example.com>"

# Push batch changes
git push origin main
```

**Step 3.3**: Monitor batch processing
```bash
# Wait for processing
sleep 30

# Verify workflow handles multiple files
LATEST_RUN=$(gh run list --repo HaldisB2B/.github --limit 1 --json databaseId --jq '.[0].databaseId')
gh run view $LATEST_RUN --repo HaldisB2B/.github --log | grep -i "files changed"

# Expected: Should show multiple files processed
```

### **Success Criteria**:
- ✅ All files processed in single workflow run
- ✅ Cross-references maintained correctly
- ✅ No file conflicts or corruption
- ✅ Batch operation completes successfully

---

## 🧹 Test Cleanup (Required)

### **Objective**: Remove test files and restore clean state

**Step 4.1**: Remove all test files
```bash
# Remove test files
rm docs/wiki/TEST_WIKI_SYNC.md
rm docs/wiki/MULTI_FILE_TEST_A.md
rm docs/wiki/MULTI_FILE_TEST_B.md

# Verify removal
ls docs/wiki/ | grep -i test
# Expected output: No test files should be listed
```

**Step 4.2**: Commit cleanup
```bash
# Commit test file removal
git add -A
git commit -m "test: Clean up wiki synchronization test files

Removing temporary test files after successful validation of wiki automation system.

🤖 Generated with [Claude Code](https://claude.ai/code)

Co-Authored-By: [Your Name] <your-email@example.com>"

# Push cleanup
git push origin main
```

**Step 4.3**: Verify cleanup workflow
```bash
# Confirm final cleanup workflow
sleep 30
gh run list --repo HaldisB2B/.github --limit 1

# Expected: Successful workflow run for cleanup
```

---

## 📊 Test Results Documentation

### **Results Summary Template**

Copy and fill out this template for your test results:

```markdown
# Wiki System Test Results

**Tester**: [Your Name]
**Date**: [Test Date]
**Duration**: [Total Time]

## Test Case Results

### Test Case 1: Basic Wiki Update
- Status: ✅ PASS / ❌ FAIL
- Workflow Trigger: ✅ PASS / ❌ FAIL
- Content Publishing: ✅ PASS / ❌ FAIL
- Notes: [Any observations]

### Test Case 2: Content Update Verification
- Status: ✅ PASS / ❌ FAIL
- Update Detection: ✅ PASS / ❌ FAIL
- Content Preservation: ✅ PASS / ❌ FAIL
- Notes: [Any observations]

### Test Case 3: Multiple File Operations
- Status: ✅ PASS / ❌ FAIL
- Batch Processing: ✅ PASS / ❌ FAIL
- Cross-References: ✅ PASS / ❌ FAIL
- Notes: [Any observations]

### Test Cleanup
- Status: ✅ COMPLETE / ❌ INCOMPLETE
- Notes: [Any observations]

## Overall Assessment
- Total Tests: 3
- Passed: [Number]
- Failed: [Number]
- Overall Status: ✅ SYSTEM READY / ❌ ISSUES FOUND

## Issues Encountered
[List any problems, errors, or unexpected behavior]

## Recommendations
[Any suggestions for improvements or concerns]
```

---

## 🚨 Troubleshooting Guide

### **Common Issues and Solutions**

**Issue 1: Workflow Not Triggering**
```bash
# Check if you're on the correct branch
git branch --show-current

# Verify file is in correct location
ls docs/wiki/

# Check for upstream branch issues
git status
```

**Issue 2: Permission Errors**
```bash
# Verify organization membership
gh api user/memberships/orgs/HaldisB2B

# Check repository access
gh repo view HaldisB2B/.github
```

**Issue 3: Workflow Fails**
```bash
# Get detailed error logs
FAILED_RUN=$(gh run list --repo HaldisB2B/.github --status failure --limit 1 --json databaseId --jq '.[0].databaseId')
gh run view $FAILED_RUN --repo HaldisB2B/.github --log
```

**Issue 4: Git Authentication Problems**
```bash
# Re-authenticate with GitHub CLI
gh auth login

# Verify authentication
gh auth status
```

### **When to Escalate**
Contact the development team if:
- ❌ Multiple workflow runs fail consistently
- ❌ Content appears corrupted or missing
- ❌ Authentication issues persist
- ❌ Any security-related concerns arise

---

## 📞 Support Contacts

**Primary Contact**: Development Team Lead  
**Secondary Contact**: DevOps Team  
**Escalation**: System Administrator  

**Documentation Repository**: `HaldisB2B/.github/docs/wiki/`  
**Workflow File**: `.github/workflows/publish-wiki.yml`  
**Issue Reporting**: GitHub Issues in HaldisB2B/.github repository

---

**🧪 Comprehensive testing procedures for HaldisB2B wiki automation system**

*This document ensures all team members can validate the wiki system functionality and provides clear procedures for testing, cleanup, and issue reporting.*

---

*Document Created: September 2025  
Last Updated: September 2025  
Next Review: October 2025  
Testing Duration: 15-20 minutes per team member*

**🤖 Generated with AI assistance following HaldisB2B testing standards**

**Co-Authored-By: Claude <noreply@anthropic.com>**