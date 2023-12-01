# -BDD---Test-with-Gherkin-Syntax

# Specification

We have a web application managing scheduled services for equipment. Services are assigned to specific technicians, who travel to the equipment location. Technicians have a checklist of activities to mark as completed in the app for each service. A completed service is supported by evidence in the form of photos.

## Scenario 1: Technicians tick off performed activities

**Scenario: Technicians tick off performed activities**
  
Given a service with these todos

| done | activity       |
|------|----------------|
| no   | Change oil     |
| yes  | Change filter  |

When a user marks the 'Change oil' activity as done

Then a toast pops up confirming that the 'Change oil' activity is completed

## Scenario 2: Technicians cannot tick off done activities

**Scenario: Technicians cannot tick off done activities**
  
Given the machine is at location "40.5453454;50.3243243"
* the browser reports location at "40.5453454;50.3243243"
* a service with these todos

| done | activity         |
|------|------------------|
| no   | Change oil       |
| yes  | Change filter    |
| yes  | Change tires     |
| yes  | Check belt wear  |

When a user clicks the 'Change filter' activity

Then no toast pops up indicating that the 'Change filter' activity is completed

When a user clicks the 'Change tires' activity

Then no toast pops up indicating that the 'Change tires' activity is completed

When a user clicks the 'Change oil' activity

Then no toast pops up indicating that the 'Change oil' activity is completed

When a user clicks the 'Check belt wear' activity

Then no toast pops up indicating that the 'Check belt wear' activity is completed

## Scenario 3: Technician can complete the whole task with the last todo

**Scenario: Technician can complete the whole task with the last todo**
  
Given a service with these todos

| done | activity         |
|------|------------------|
| no   | Change oil       |
| yes  | Change filter    |
| yes  | Change tires     |
| yes  | Check belt wear  |

When a user marks the 'Change oil' activity as done

Then a toast pops up confirming that the entire service is completed
