---
uid: eisk-webapi-testing-services
---

# Testing Services

Test business logic located in [domain service](xref:eisk-webapi-logical-layers) can be done with different approaches.

## Integration Tests Only

* Domain service rules are tested by creating in-memory database. 
* No integration tests are performed against data service.
* Provides more confidence on the written code, as rules are tested against database.
* Default testing strategy of Eisk Web Api for domain service testing.

        [Fact]
        public virtual void Add_ValidDomainPassed_ShouldReturnDomainAfterCreation()
        {
            //Arrange
            var inputDomain = Factory_Entity();
            var domainService = GetServiceInstance();

            //Act
            var returnedDomain = domainService.Add(inputDomain);

            //Assert
            Assert.NotNull(returnedDomain);
            Assert.NotEqual(default(TId), GetIdValueFromEntity(returnedDomain));
        }
		
## Unit Tests Only

Tests domain services using mock frameworks and verifies the actions (such as validations that requires accessing database etc) are performed as expected.

## Unit + Integration Tests

### Domain Service Unit Tests

Domain service rules are tested by creating mocks.

### Data Service Integration Tests

Tests the data services that uses advanced functionalities provided by underlying ORM. The tests are performed on top of in-memory database or actual physical database.

        [Fact]
        public virtual void Add_ValidDomainWithRandomIdPassed_ShouldReturnDomainAfterCreation()
        {
            //Arrange
            var inputEntity = Factory_Entity();
            SetIdValueToEntity(inputEntity, IntegerValueGenerator.RandomInt;);
            var dataService = GetServiceInstance();

            //Act
            var returnedEntity = dataService.Add(inputEntity);

            //Assert
            Assert.NotNull(returnedEntity);
            Assert.NotEqual(default(TId), GetIdValueFromEntity(returnedEntity));
        }

