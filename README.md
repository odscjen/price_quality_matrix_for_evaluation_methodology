# Description
This Extension is proposed for all open and restricted tender procedures to decompose Price and Quality Criteria to atomic requirements. This Extension allows to maintain all Price and Quality Criteria in accordance with EBRD UNCITRAL Price-Quality Matrix for Open/Restricted Tender. Main approach - the Requirements Extension is selected due to use of this model (Criterion -> Requirement Group -> Requirements) in European Bank for Reconstruction and Development digital tools, which are intended to monitor Tender procedures automatically and keep procedures transparent. 

This leads to use Requirement Extension, based on CCCEV model (see below) as framework, on the basis of EBRD UNCITRAL Price-Quality Matrix for Open/Restricted Tender. In this case, all required information can be stored and handled easily. All Criteria, Requirement Groups and Requirements are taken from EBRD UNCITRAL Price-Quality Matrix for Open/Restricted Tender. Requirements for Quality Criteria can be expressed as a questions and are not the mandatory and can be changed and updated if needed (as well as number of requirements). Just add it in accordance with corresponding Requirement Groups.  Full model in table view with all connections is presented in Standard Bidding Document folder, in Excel file.

This approach allows to use existing EBRD digital tools for Tender monitoring for all countries and Procurement Systems. The main difference with existing Requirements Extension is mandatory naming for Criteria, Requirement Groups and Requirements (only in case of Price, it is free structure for Quality), presented in corresponding codelists. 




# Requirements

The requirements extension is based on the EU's [Core Criterion and Core Evidence Vocabulary (CCCEV)](https://joinup.ec.europa.eu/node/153001) model for communicating criteria and responses.

The extension is designed to allow procuring entities or buyers to express criteria, relating to either items being procured or bidders themselves, as structured data.

Criteria can be responded to either by bidders, buyers or procuring entities, for example a buyer may respond with information about an item whilst a procuring entity may respond with information on whether a bidder is disbarred.

Criteria list is designed on the basis of EBRD UNCITRAL Price-Quality Matrix for Open/Restricted Tender. 


## CCCEV Model

The CCCEV model defines the following concepts:

**Criterion**
A criterion represents a rule or principle used to judge, evaluate or assess either an item or bidder. A criterion is satisfied when one or more of it's requirement groups are satisfied. Criteria are taken from 

**Requirement Group**
A requirement group is a collection of one or more individual requirements. A requirement group is satisfied when all of it's requirements are satisfied.

**Requirement**
An atomic requirement which can be expressed as either an expected value or a range of accepted values.
Requirements are based on the EBRD Bidder Qualification Forms.
In this version under 'Requirements' we understand all information, can be presented in separate cells of Qualification Forms. 

**Requirement Response**
A requirements response is an assertion that responds to a specific requirement.

Therefore the CCCEV model can be used to express both **AND** conditions, where a group of requirements must be met to satisfy a criterion, and **OR** conditions, where there are alternative requirements that can satisfy a criterion.

## Schema

The extension introduces a new building block for each of the concepts described above, these are added to the following locations in the OCDS schema:

* *tender.criteria* - an array of criteria
* *tender.criteria.requirementGroups* - an array of requirement groups
* *tender.criteria.requirementGroups.requirements* - an array of requirements
* *bids.requirementResponses* - an array of requirement responses (Note: depends on *bid* extension)
* *awards.requirementResponses* - an array of requirements responses
* *contracts.requirementResponses* - an array or requirement responses

## Example

Below is an example of requirements specified against both an item and a bidder which demonstrates both **AND** and **OR** conditions:

```json
    "tender": {"criteria" : [{        
      "id": "1",
      "title": "Acqusistion/Initial Capital Expenditure",
      "description": "Decomposed data for Acqusistion/Initial Capital Expenditure",
      "relatesTo": "tenderer",
      "source": "tenderer",
      "requirementGroups": [
        {
          "id": "1",
          "title": "PRICE OF GOODS/PROVISION OF SERVICE",
          "requirements": [
            {
              "id": "1",
              "title": "Material",
              "description": "Costs for Materials",
              "dataType": "value",
              "period": {
                "startDate": "2013-04-03T00:00:00Z",
                "endDate": "2014-04-03T00:00:00Z"
              },
              "value": {"amount": "5541314.23", "currency":"EUR"}
            },
            {
              "id": "2",
              "title": "Labour/Hourly Rate",
              "description": "Costs for Labour/Hourly Rate",
              "dataType": "value",
              "period": {
                "startDate": "2013-04-03T00:00:00Z",
                "endDate": "2014-04-03T00:00:00Z"
              },
              "value": {"amount": "5541314.23", "currency":"EUR"}
            },
            {
              "id": "3",
              "title": "Overheads",
              "description": "Costs for Overheads",
              "dataType": "value",
              "period": {
                "startDate": "2013-04-03T00:00:00Z",
                "endDate": "2014-04-03T00:00:00Z"
              },
             "value": {"amount": "5541314.23", "currency":"EUR"}
            },
            {
              "id": "4",
              "title": "Packaging",
              "description": "Costs for Packaging",
              "dataType": "value",
              "period": {
                "startDate": "2013-04-03T00:00:00Z",
                "endDate": "2014-04-03T00:00:00Z"
              },
              "value": {"amount": "5541314.23", "currency":"EUR"}
            },
            {
              "id": "5",
              "title": "Profit",
              "description": "Profit amount",
              "dataType": "value",
              "period": {
                "startDate": "2013-04-03T00:00:00Z",
                "endDate": "2014-04-03T00:00:00Z"
              },
              "value": {"amount": "5541314.23", "currency":"EUR"}
            }
          ]
        },
        {
          "id": "2",
          "title": "COMMISSIONING COSTS",
          "requirements": [
            {
              "id": "1",
              "title": "Delivery",
              "description": "Costs for Delivery",
              "dataType": "value",
              "period": {
                "startDate": "2013-04-03T00:00:00Z",
                "endDate": "2014-04-03T00:00:00Z"
              },
              "value": {"amount": "5541314.23", "currency":"EUR"}
            },
            {
              "id": "2",
              "title": "Installation",
              "description": "Costs for Installation",
              "dataType": "value",
              "period": {
                "startDate": "2013-04-03T00:00:00Z",
                "endDate": "2014-04-03T00:00:00Z"
              },
              "value": {"amount": "5541314.23", "currency":"EUR"}
            },
            {
              "id": "3",
              "title": "Training",
              "description": "Costs for Training",
              "dataType": "value",
              "period": {
                "startDate": "2013-04-03T00:00:00Z",
                "endDate": "2014-04-03T00:00:00Z"
              },
              "value": {"amount": "5541314.23", "currency":"EUR"}
            },
            {
              "id": "4",
              "title": "Travel",
              "description": "Costs for travel",
              "dataType": "value",
              "period": {
                "startDate": "2013-04-03T00:00:00Z",
                "endDate": "2014-04-03T00:00:00Z"
              },
              "value": {"amount": "5541314.23", "currency":"EUR"}
            }
          ]
        }
      ]
    }
]
}
```

Below is an example of responses which meet the above requirements:

```json
  "bids": {
      "details": [
        {
          "id": "1",
          "requirementResponses": [
            {
              "id": "T1",
              "value": { # new type
                "amount": 5541314.23,
                "currency": "EUR"
              },
              "period": {
                "startDate": "2013-04-03T00:00:00Z",
                "endDate": "2014-04-03T00:00:00Z"
              }
              "requirement": {
                "id": "T1",
                "title": "FY 1"
              }
            },
            {
              "id": "T2",
              "value": {
                "amount": 9231341.00,
                "currency": "EUR"
              },
              "period": {
                "startDate": "2014-04-03T00:00:00Z",
                "endDate": "2015-04-03T00:00:00Z"
              }
              "requirement": {
                "id": "T2",
                "title": "FY 2"
              }
            },
            {
              "id": "T3",
              "value": {
                "amount": 9941927.15,
                "currency": "EUR"
              },
              "period": {
                "startDate": "2015-04-03T00:00:00Z",
                "endDate": "2016-04-03T00:00:00Z"
              }
              "requirement": {
                "id": "T3",
                "title": "FY 3"
              }
            }
          ]
        }
      ]
    }
```

## Further extensions

The CCCEV model also defines a number of additional concepts including **formalFrameworks**, used to specify the legal instruments from criteria are derived, **evidence**, used both to specify and provide the evidence required to support a requirement response, and additional properties of *requirements* such as **certificationLevel** which are not currently implemented in this extension.

This extension does not describe formulae for calculating computed values, nor does it describe whether data should be published openly or not.


