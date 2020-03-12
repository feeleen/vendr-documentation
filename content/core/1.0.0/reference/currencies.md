---
title: Currencies
description: Currency related APIs in Vendr, the eCommerce solution for Umbraco v8+
---

## Currency Service

### ICurrencyService

#### GetCurrencies

Gets a collection of all Currency entities in a Store

***Signature:***

````csharp
IEnumerable<CurrencyReadOnly> GetCurrencies(Guid storeId);
````

***Parameters:***

| Type | Name | Description |
| ---- | ----- | ----------- |
| `Guid` | `storeId` | The ID of the Store the Currencies belong to |

***Returns:***

| Type | Description |
| ---- | ----------- |
| `IEnumerable<CurrencyReadOnly>` | A list of read only Currency entities |

#### GetCurrenciesAllowedIn

Gets a collection of all Currency allowed in a Country

***Signature:***

````csharp
IEnumerable<CurrencyReadOnly> GetCurrenciesAllowedIn(Guid countryId);
````

***Parameters:***

| Type | Name | Description |
| ---- | ----- | ----------- |
| `Guid` | `countryId` | The ID of the Country the Currencies are allowed in |

***Returns:***

| Type | Description |
| ---- | ----------- |
| `IEnumerable<CurrencyReadOnly>` | A list of read only Currency entities |

#### GetCurrency

Gets a specific Currency entity

***Signature:***

````csharp
CurrencyReadOnly GetCurrency(Guid id);
````

***Parameters:***

| Type | Name | Description |
| ---- | ----- | ----------- |
| `Guid` | `id` | The ID of the Currency to fetch  |

***Returns:***

| Type | Description |
| ---- | ----------- |
| `CurrencyReadOnly` | A read only Currency entity matching the provided criteria  |

---

***Signature:***

````csharp
CurrencyReadOnly GetCurrency(Guid storeId, string code);
````

***Parameters:***

| Type | Name | Description |
| ---- | ----- | ----------- |
| `Guid` | `storeId` | The ID of the Store the Currencies belong to |
| `string` | `code` | The Code of the Currency to fetch  |

***Returns:***

| Type | Description |
| ---- | ----------- |
| `CurrencyReadOnly` | A read only Currency entity matching the provided criteria  |

#### SaveCurrency

Persists the given Currency to the database

***Signature:***

````csharp
void SaveCurrency(Currency Currency);
````

***Parameters:***

| Type | Name | Description |
| ---- | ----- | ----------- |
| `Currency` | `Currency` | The Currency to save  |

#### DeleteCurrency

Deletes the given Currency

***Signature:***

````csharp
void DeleteCurrency(Guid CurrencyId);
````

***Parameters:***

| Type | Name | Description |
| ---- | ----- | ----------- |
| `Guid` | `CurrencyId` | The ID of the Currency to delete |

---

***Signature:***

````csharp
void DeleteCurrency(Currency entity);
````

***Parameters:***

| Type | Name | Description |
| ---- | ----- | ----------- |
| `Currency` | `entity` | The Currency to delete |

#### SortCurrencies

Sorted the Currencies with the given IDs, by the given ID sequence

***Signature:***

````csharp
void SortCurrencies(Guid[] sortedIds);
````

***Parameters:***

| Type | Name | Description |
| ---- | ----- | ----------- |
| `Guid[]` | `sortedIds` | Sequence of Currency IDs to sort in the given order |

### CurrencyService

**Description:** Default implementation of the [Vendr Currency Service Interface](#icurrencyservice)  
**Namespace:** Vendr.Core.Services  
**Assembly:** Vendr.Core

<div class="mb-48"></div>

## Currency Entities

### CurrencyReadOnly

**Description:** Read Only Currency entity  
**Namespace:** Vendr.Core.Models  
**Assembly:** Vendr.Core

#### Properties

| Type | Name | Description |
| ---- | ---- | ----------- |
| `Guid` | `Id` | The Currency unique ID |
| `Guid` | `StoreId` | The ID of the Store this Currency belongs to |
| `string` | `Code` | A unique Code for the Currency |
| `string` | `Name` | The Name of the Currency |
| `string` | `CultureName` | The Culture Name of the Currency |
| `string` | `FormatTemplate` | The custom string format template for formatting the Currency |
| `IReadOnlyCollection <AllowedCountry>` | `AllowedCountries` | A collection of Countries this Currency is allowed in |
| `int` | `SortOrder` | The Sort Order of the Currency |
| `bool` | `IsDeleted` | Flag indicating whether the Currency is deleted |

#### IsAllowedInCountry
Checks whether the given Country is allowed by the Currency

***Signature:***

````csharp
bool IsAllowedInCountry(CountryReadOnly country);
````

***Parameters:***

| Type | Name | Description |
| ---- | ----- | ----------- |
| `CountryReadOnly` | `country` | The Country to check if allowed by the Currency |

***Returns:***

| Type | Description |
| ---- | ----------- |
| `bool` | Flag indicating whether the Country is allowed by the Currency |

---

***Signature:***

````csharp
bool IsAllowedInCountry(Guid countryId);
````

***Parameters:***

| Type | Name | Description |
| ---- | ----- | ----------- |
| `Guid` | `countryId` | The ID of the Country to check if allowed by the Currency |

***Returns:***

| Type | Description |
| ---- | ----------- |
| `bool` | Flag indicating whether the Country is allowed by the Currency |

#### AsWritable
Gets a writable version of the associated Currency

***Signature:***

````csharp
Currency AsWritable(IUnitOfWork uow);
````

***Parameters:***

| Type | Name | Description |
| ---- | ----- | ----------- |
| `IUnitOfWork` | `uow` | An active Unit of Work to associate with this writable entity |

***Returns:***

| Type | Description |
| ---- | ----------- |
| `Currency` | A writable version of the Currency |

### Currency

**Description:** Writable Currency entity  
**Namespace:** Vendr.Core.Models  
**Assembly:** Vendr.Core  
**Inherits:** [ CurrencyReadOnly](#currencyreadonly) 

#### Create
Creates a Currency entity

***Signature:***

````csharp
static Currency Create(IUnitOfWork uow);
````

***Parameters:***

| Type | Name | Description |
| ---- | ----- | ----------- |
| `IUnitOfWork` | `uow` | An active Unit of Work to associate with this writable entity |

***Returns:***

| Type | Description |
| ---- | ----------- |
| `Currency` | A writable Currency |

#### AsReadOnly
Converts a writable Currency into a read only Currency

***Signature:***

````csharp
CurrencyReadOnly AsReadOnly();
````

***Returns:***

| Type | Description |
| ---- | ----------- |
| `CurrencyReadOnly` | A read only version of the Currency |

<div class="mb-48"></div>

## Currency Owned Entities

<div class="mb-48"></div>

## Currency Events

### Validation Events

#### ValidateCurrencyCreate

**Description:** Validation event fired when an Currency is being created  
**Namespace:** Vendr.Core.Events.Validation   
**Assembly:** Vendr.Core

***Properties:***

| Type | Name | Description |
| ---- | ---- | ----------- |
| `CurrencyReadOnly` | `Currency` | The Currency associated with this event |

#### ValidateCurrencyUpdate

**Description:** Validation event fired when an Currency is being updated  
**Namespace:** Vendr.Core.Events.Validation   
**Assembly:** Vendr.Core

***Properties:***

| Type | Name | Description |
| ---- | ---- | ----------- |
| `CurrencyReadOnly` | `Currency` | The Currency associated with this event |

#### ValidateCurrencySave

**Description:** Validation event fired when an Currency is being saved  
**Namespace:** Vendr.Core.Events.Validation   
**Assembly:** Vendr.Core

***Properties:***

| Type | Name | Description |
| ---- | ---- | ----------- |
| `CurrencyReadOnly` | `Currency` | The Currency associated with this event |

#### ValidateCurrencyDelete

**Description:** Validation event fired when an Currency is being deleted  
**Namespace:** Vendr.Core.Events.Validation   
**Assembly:** Vendr.Core

***Properties:***

| Type | Name | Description |
| ---- | ---- | ----------- |
| `CurrencyReadOnly` | `Currency` | The Currency associated with this event |

### Notification Events

#### CurrencyCreatingNotification

**Description:** Notification event fired before an Currency is created   
**Namespace:** Vendr.Core.Events.Notification   
**Assembly:** Vendr.Core

***Properties:***

| Type | Name | Description |
| ---- | ---- | ----------- |
| `Currency` | `Currency` | The Currency associated with this event |

#### CurrencyCreatedNotification

**Description:** Notification event fired after an Currency is created   
**Namespace:** Vendr.Core.Events.Notification   
**Assembly:** Vendr.Core

***Properties:***

| Type | Name | Description |
| ---- | ---- | ----------- |
| `CurrencyReadOnly` | `Currency` | The Currency associated with this event |

#### CurrencyUpdatingNotification

**Description:** Notification event fired before an Currency is updated   
**Namespace:** Vendr.Core.Events.Notification   
**Assembly:** Vendr.Core

***Properties:***

| Type | Name | Description |
| ---- | ---- | ----------- |
| `Currency` | `Currency` | The Currency associated with this event |

#### CurrencyUpdatedNotification

**Description:** Notification event fired after an Currency is updated   
**Namespace:** Vendr.Core.Events.Notification   
**Assembly:** Vendr.Core

***Properties:***

| Type | Name | Description |
| ---- | ---- | ----------- |
| `CurrencyReadOnly` | `Currency` | The Currency associated with this event |

#### CurrencySavingNotification

**Description:** Notification event fired before an Currency is saved   
**Namespace:** Vendr.Core.Events.Notification   
**Assembly:** Vendr.Core

***Properties:***

| Type | Name | Description |
| ---- | ---- | ----------- |
| `Currency` | `Currency` | The Currency associated with this event |

#### CurrencySavedNotification

**Description:** Notification event fired after an Currency is saved   
**Namespace:** Vendr.Core.Events.Notification   
**Assembly:** Vendr.Core

***Properties:***

| Type | Name | Description |
| ---- | ---- | ----------- |
| `CurrencyReadOnly` | `Currency` | The Currency associated with this event |

#### CurrencyDeletingNotification

**Description:** Notification event fired before an Currency is deleted   
**Namespace:** Vendr.Core.Events.Notification   
**Assembly:** Vendr.Core

***Properties:***

| Type | Name | Description |
| ---- | ---- | ----------- |
| `Currency` | `Currency` | The Currency associated with this event |

#### CurrencyDeletedNotification

**Description:** Notification event fired after an Currency is deleted   
**Namespace:** Vendr.Core.Events.Notification   
**Assembly:** Vendr.Core

***Properties:***

| Type | Name | Description |
| ---- | ---- | ----------- |
| `CurrencyReadOnly` | `Currency` | The Currency associated with this event |