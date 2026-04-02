---
name: Testing
description: Skill for writing and running effective tests
---

# Testing Skill

Guidelines for writing, running, and maintaining a high-quality test suite.

## When to Use This Skill

- When adding new features (test-first approach)
- When fixing bugs (write a test to reproduce, then fix)
- When refactoring (ensure behavior remains the same)

## Testing Pyramid

```
         /  E2E  \          ← Few, slow, comprehensive
        / Integration \     ← Medium, test interactions between components
       /   Unit Tests   \   ← Many, fast, focused
```

## Test Writing Guidelines

### Unit Tests
- Test only one unit/function per test case
- Use the naming pattern: `test_<function>_<condition>_<expected_result>`
- Follow the Arrange → Act → Assert pattern
- Mock external dependencies

```python
# Python example
def test_calculate_discount_above_threshold_returns_ten_percent():
    # Arrange
    price = 150.00
    threshold = 100.00

    # Act
    result = calculate_discount(price, threshold)

    # Assert
    assert result == 15.00
```

```javascript
// JavaScript example
describe('calculateDiscount', () => {
  it('should return 10% discount when price is above threshold', () => {
    // Arrange
    const price = 150.00;
    const threshold = 100.00;

    // Act
    const result = calculateDiscount(price, threshold);

    // Assert
    expect(result).toBe(15.00);
  });
});
```

### Integration Tests
- Test interactions between components/services
- Use a test database (not production)
- Clean up data after tests complete
- Test both happy path and error path

### End-to-End Tests
- Test critical user flows
- Use the page object pattern for UI tests
- Set reasonable timeouts
- Run in the CI/CD pipeline

## Test Quality Checklist

- [ ] Tests cover the happy path
- [ ] Tests cover edge cases (null, empty, boundary values)
- [ ] Tests cover error/exception handling
- [ ] Test names are descriptive and clear
- [ ] Tests are independent and don't depend on each other
- [ ] Tests can be run repeatedly (deterministic)
- [ ] No tests depend on external services
- [ ] Mocking is used appropriately (not over-mocked)

## Running Tests

```bash
# Adjust based on the project's tech stack
npm test              # JavaScript/Node.js
pytest                # Python
go test ./...         # Go
mvn test              # Java/Maven
```
