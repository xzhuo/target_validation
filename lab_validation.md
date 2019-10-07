## Lab_validation:

```cypher
WITH [
  {
    institute: "North Carolina State University",
    mailing_address: "112 Derieux Place, Raleigh, North Carolina 27606",
    grant_number: "U01ES026717",
    department: "Department of Biological Sciences",
    principal_investigator: "David Aylor"
  },
  {
    institute: "Johns Hopkins University",
    mailing_address: "615 North Wolfe Street, Baltimore, Maryland 21205",
    grant_number: "U01ES026721",
    department: "Department of Environmental Health and Engineering",
    principal_investigator: "Shyam Biswal"
  },
  {
    institute: "University of Pennsylvania",
    mailing_address: "3400 Civic Boulevard, Philadelphia, Pennsylvania 19104",
    grant_number: "U01ES026719",
    department: "The Epigenetics Institute",
    principal_investigator: "Marisa Bartolomei"
  },
  {
    institute: "University of Michigan",
    mailing_address: "1415 Washington Heights, Ann Arbor, Michigan 48109",
    grant_number: "U01ES026697",
    department: "Department of Environmental Health Sciences",
    principal_investigator: "Dana Dolinoy"
  },
  {
    institute: "Baylor College of Medicine",
    mailing_address: "One Baylor Plaza, Houston, Texas 77030",
    grant_number: "U01ES026719",
    department: "Center for Precision Environmental Health",
    principal_investigator: "Cheryl Walker"
  },
  {
    institute: "Johns Hopkins University",
    mailing_address: "615 North Wolfe Street, Baltimore, Maryland 21205",
    grant_number: "U01ES026721",
    department: "Department of Environmental Health and Engineering",
    principal_investigator: "Zhibin Wang"
  },
  {
    institute: "University of Chicago",
    mailing_address: "5841 South Maryland Avenue, Chicago, Illinois 60637",
    grant_number: "U01ES026718",
    department: "Department of Pulmonary and Critical Care Medicine",
    principal_investigator: "Gokhan Mutlu"
  },
  {
    institute: "Washington University in St. Louis",
    mailing_address: "4515 McKinley Avenue, Saint Louis, Missouri 63110",
    grant_number: "U24ES026699",
    department: "Department of Genetics",
    principal_investigator: "Ting Wang"
  }
] AS lab_list
MATCH (l:lab) WITH l, lab_list AS lab_list, {principal_investigator:l.principal_investigator, institute:l.institute, department:l.department, mailing_address:l.mailing_address, grant_number:l.grant_number} AS lab_map
WHERE NOT lab_map IN lab_list RETURN "accession number " + l.accession + " did not match the approved list of labs."
```