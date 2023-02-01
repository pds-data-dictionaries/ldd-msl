PDS4 Mars Science Laboratory Mission Dictionary User's Guide  
2023-02-01
Jennifer Ward

# Introduction
   1. Purpose of this User's Guide
   - This User's Guide provides an overview of the MSL Mission Data Dictionary. It details how to include the dictionary in a PDS4 label, describes the organization of classes and attributes, provides definitions of the classes and attributes, and lists examples of labels that use it.
   2. Audience
   - This User's Guide should be useful to data providers intending to archive MSL data with PDS as well as PDS Nodes who are working with these data providers.

# Overview of the MSL Mission Dictionary

The MSL Mission Dictionary contains classes, attributes, and rules specific to the MSL mission and its instruments. 
Steward: Jennifer Ward, PDS Geosciences Node, geosci@wunder.wustl.edu

# How to Include the MSL Mission Dictionary in a PDS4 Label

The dictionary consists of a set of files with names in the form PDS4_MSL_xxxx_yyyy.ext, where
- xxxx = the PDS4 Information Model version, e.g. 1H00 
- yyyy = the MSL Mission Dictionary version, e.g. 1000

and the file extensions are

- .csv = A comma-separated value table of dictionary attributes 
- .JSON = The dictionary contents in JSON format 
- .sch = The dictionary "rules" as an XML Schematron file 
- .txt = The report generated when the dictionary was built 
- .xml = The PDS4 label that describes this set of files 
- .xsd = The dictionary contents as an XML schema file

Only the schema and Schematron files are needed for validating a PDS4 label.

The latest version of this dictionary may be found on the PDS web site at https://pds.nasa.gov/datastandards/dictionaries/index-missions.shtml#msl.

The following is an example showing the use of this dictionary in a PDS4 label.

```
   <?xml version="1.0" encoding="UTF-8"?>
   <?xml-model href="https://pds.nasa.gov/pds4/pds/v1/PDS4_PDS_1I00.sch" schematypens="http://purl.oclc.org/dsdl/schematron"?>
   <?xml-model href="https://pds.nasa.gov/pds4/mission/mro/v1/PDS4_MSL_1H00_1000.sch" schematypens="http://purl.oclc.org/dsdl/schematron"?>    
   <Product_Observational xmlns="http://pds.nasa.gov/pds4/pds/v1"
       xmlns:mro="http://pds.nasa.gov/pds4/mission/msl/v1"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://pds.nasa.gov/pds4/pds/v1           https://pds.nasa.gov/pds4/pds/v1/PDS4_PDS_1I00.xsd
                           http://pds.nasa.gov/pds4/mission/msl/v1   https://pds.nasa.gov/pds4/mission/msl/v1/PDS4_MRO_1H00_1000.xsd">
```

The following is an example showing the location of the MSL dictionary classes and attributes in a PDS4 label.

```
<Observation_Area>
    ...
       <Mission_Area>
        <msl:MSL_Parameters>
          <msl:Observation_Information>
            <msl:release_number>
            <msl:product_type>
            <msl:mission_phase_name>
            <msl:spacecraft_clock_start>
            <msl:spacecraft_clock_stop>
            <msl:spacecraft_clock_partition>
            <msl:sol_number>
            <msl:start_local_true_solar_time>
            <msl:start_local_true_solar_time_sol>
            <msl:stop_local_true_solar_time>
            <msl:stop_local_true_solar_time_sol>            
            <msl:active_flight_computer>
            <msl:producer_institution_name>
        </msl:MSL_Parameters>
       </Mission_Area>
        ...         
```

The namespace for the MSL Mission Dictionary is http://pds.nasa.gov/pds4/mission/msl/v1, abbreviated "msl:".

# Organization of Classes and Attributes

See the [schematic](../../MSL_LDD_diagram.png) for a visual representation of the classes and attributes.

Below is a list showing the hierarchy of classes in order of appearance in the PDS4 label. 
See the Definitions section for complete definitions.

- MSL_Parameters class
    - Observation_Information class

Below are lists showing the hierarchy of class attributes in order of appearance in the PDS4 label. 
See the Definitions section for complete definitions.

## MSL_Parameters Class
- Observation_Information

## Observation_Information Class
- release_number
- product_type
- mission_phase_name
- spacecraft_clock_start
- spacecraft_clock_stop
- spacecraft_clock_partition
- sol_number
- start_local_true_solar_time
- start_local_true_solar_time_sol
- stop_local_true_solar_time
- stop_local_true_solar_time_sol>           
- active_flight_computer
- producer_institution_name

# Definitions

Classes (in alphabetical order)

*MSL_Parameters*
- The MSL_Parameters class is a superclass containing all MSL mission classes.
- Minimum occurrences: 1
- Maximum occurrences: 1

*Observation_Information*
- The Observation_Information class provides information about a science observation.
- Minimum occurrences: 1
- Maximum occurrences: 1

Attributes (in alphabetical order)

*active_flight_computer*
The active_flight_computer indicates which flight computer "string" (separate sets of electronics) was active when a product was acquired. For MSL there are two redundant flight computers called "strings", also known as Rover Compute Elements (RCEs). Either string, A or B, may be active at any given time.
- PDS4 data type: ASCII_Short_String_Collapsed
- Valid values:
  - A - The value "A" indicates flight computer A.
  - B - The value "B" indicates flight computer B.
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No

*mission_phase_name*
The mission_phase_name identifies a time period within the mission.
- PDS4 data type: ASCII_Short_String_Preserved
- Valid values:
  - CRUISE AND APPROACH - The cruise and approach phase began when the launch phase ended, and ended 30 minutes prior to entry into the Mars atmosphere.
          Mission Phase Start Time : 2011-11-26
          Mission Phase Stop Time : 2012-08-06
  - DEVELOPMENT - The development phase began in October 2003 with concept and technology development, followed by preliminary design and technology development completion from March 2006 through September 2006, final design and fabrication from September 2006 through January 2008, and system assembly, integration, and test from late January 2008 until launch on November 26, 2011.
          Mission Phase Start Time : 2003-10-01
          Mission Phase Stop Time : 2011-11-26
  - ENTRY, DESCENT, AND LANDING - The entry, descent, and landing (EDL) phase began when the Cruise and Approach Phase was over (30 minutes before atmospheric entry), and ended when the rover reached a thermally stable, positive energy balance, commandable configuration on the surface of Mars.
          Mission Phase Start Time : 2012-08-06
          Mission Phase Stop Time : 2012-08-06
  - EXTENDED SURFACE MISSION - The extended surface phase began on Sol 764.
          Mission Phase Start Time : 2014-09-29
          Mission Phase Stop Time : UNK
  - LAUNCH - The launch phase began when the spacecraft switched to internal power prior to launch and ended when the spacecraft reached a thermally stable commandable configuration after separation from the launch vehicle upper stage.
          Mission Phase Start Time : 2011-11-26
          Mission Phase Stop Time : 2011-11-26
  - PRIMARY SURFACE MISSION - The primary surface phase began when the EDL phase was over and ended on sol 763.
          Mission Phase Start Time : 2012-08-06
          Mission Phase Stop Time : 2014-09-28
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No

*producer_institution_name*
The producer_institution_name specifies the identity of the facility or institution that produced the product.
- PDS4 data type: ASCII_Short_String_Preserved
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No

*product_type*
The product_type element identifies a group of data products within a collection that have some property in common, such as processing level, resolution, or instrument-specific setting.
- PDS4 data type: ASCII_Short_String_Collapsed
- Valid values:
  - APXS_EDR - APXS Experiment Data Records.
  - APXS_RSP - APXS summed X-ray spectra.
  - APXS_RWP - APXS oxide abundance data.
  - CHEMCAM-CCS - ChemCam LIBS Intermediate Clean Calibrated Spectra RDR data.
  - CHEMCAM-MOC - ChemCam LIBS Multivariate Prediction of Oxide Composition RDR data.
  - CHEMCAM-PSV - ChemCam LIBS Passive RDR data.
  - CHEMCAM-RDR - ChemCam Initial LIBS Spectrum RDR data.
  - CHEMCAM-TEC - ChemCam LIBS Trace Element Concentration RDR data.
  - CHEMIN_ECC - CheMin CCD Frame Experiment Data Record (EDR) data.
  - CHEMIN_ED1 - CheMin Diffraction Single Experiment Data Record (EDR) data.
  - CHEMIN_EDA - CheMin Diffraction All Experiment Data Record (EDR) data.
  - CHEMIN_EDS - CheMin Diffraction Split Experiment Data Record (EDR) data.
  - CHEMIN_EE1 - CheMin Energy Single Experiment Data Record (EDR) data.
  - CHEMIN_EEA - CheMin Energy All Experiment Data Record (EDR) data.
  - CHEMIN_EES - CheMin Energy Split Experiment Data Record (EDR) data.
  - CHEMIN_EFM - CheMin Film Experiment Data Record (EDR) data.
  - CHEMIN_EHK - CheMin Housekeeping N Experiment Data Record (EDR) data.
  - CHEMIN_ETR - CheMin Transmit Raw Experiment Data Record (EDR) data.
  - CHEMIN_MIN - CheMin Mineral identifications and abundances Reduced Data Record (RDR) data.
  - CHEMIN_RD1 - CheMin Diffraction Single, windowed K-alpha (rarely K-beta) Reduced Data Record (RDR) data.
  - CHEMIN_RDA - CheMin Diffraction All, windowed K-alpha (rarely K-beta) Reduced Data Record (RDR) data.
  - CHEMIN_RDF - CheMin Diffraction, Film Mode, Reduced Data Record (RDR) data.
  - CHEMIN_RDS - CheMin Diffraction Split, windowed K-alpha (rarely K-beta) Reduced Data Record (RDR) data.
  - CHEMIN_RE1 - CheMin Energy Single Reduced Data Record (RDR) data.
  - CHEMIN_REA - CheMin Energy All Reduced Data Record (RDR) data.
  - CHEMIN_RES - CheMin Energy Split Reduced Data Record (RDR) data.
  - CHEMIN_RTR - CheMin Diffraction All, Raw, Reduced Data Record (RDR) data.
  - DAN_ACTIVE - DAN ACTIVE mode (neutron pulses are produced and science observations collected) Experiment Data Record (EDR) data.
  - DAN_PASSIVE - DAN PASSIVE mode (background observations collected) Experiment Data Record (EDR) data.
  - DAN_RDR_AA - DAN Averaged Active Reduced Data Record (RDR) data.
  - DAN_RDR_AC - DAN Derived Active Reduced Data Record (RDR) data.
  - DAN_RDR_AP - DAN Averaged Passive Reduced Data Record (RDR) data.
  - DAN_RDR_EN - DAN Derived Engineering Reduced Data Record (RDR) data.
  - DAN_RDR_PA - DAN Derived Passive Reduced Data Record (RDR) data.
  - DAN_STANDBY - DAN STANDBY mode (low voltage electronics are on, no science observations) Experiment Data Record (EDR) data.
  - Mastcam_Photometry_Cube - Mastcam derived photometry cube data.
  - RAD_EDR - RAD Experiment Data Record (EDR) data.
  - RAD_RDR - RAD Reduced Data Record (RDR) data.
  - SAM_RDR - SAM Reduced Data Record (RDR) data.
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No

*release_number*
The release_number element is the identifier of a scheduled release of MSL data from PDS. The first MSL data release has release_number "0001". The release_number for a given product is always the first release in which it appears, and does not change if the product is revised later.
- PDS4 data type: ASCII_Short_String_Collapsed
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum characters: 4

*sol_number*
Sol_number is the number of the Mars day on which an observation was acquired. Landing day is Sol 0.
- PDS4 data type: ASCII_Integer
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 0

*spacecraft_clock_partition*
The spacecraft_clock_partition provides the clock partition active for the spacecraft_clock_start and spacecraft_clock_stop attributes. This attribute may be used when the spacecraft_clock values do not include a partition number.
- PDS4 data type: ASCII_Integer
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 1

*spacecraft_clock_start*
The spacecraft_clock_start is the value of the spacecraft clock at the beginning of an observation, in seconds. Values are formed according to the pattern [p/]dddddddddd[.fffffffff], where p is an optional partition number, dddddddddd is a whole number of seconds up to 10 digits, and .fffffffff is an optional fraction of a second up to 9 digits. The whole number and fraction are separated by a period. If a partition number and slash are not present, then the attribute spacecraft_clock_partition must be used.
- PDS4 data type: ASCII_Short_String_Collapsed
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Formation rule: [p/]dddddddddd[.fffffffff] - The spacecraft clock value is an integer with no more than 10 digits, optionally preceded by a clock partition number and forward slash, and optionally followed by a fractional value. If the fractional value is present, it must be separated from the whole number by a period, and may have up to 9 digits. If a partition number and slash are not present, then the attribute spacecraft_clock_partition must be used.
- Minimum characters: 1
- Maximum characters: 19
- Pattern: ([1-9]/)?[0-9]{1,10}(\.[0-9]{1,9})?

*spacecraft_clock_stop*
The spacecraft_clock_stop is the value of the spacecraft clock at the end of an observation, in seconds. Values are formed according to the pattern [p/]dddddddddd[.fffffffff], where p is an optional partition number, dddddddddd is a whole number of seconds up to 10 digits, and .fffffffff is an optional fraction of a second up to 9 digits. The whole number and fraction are separated by a period. If a partition number and slash are not present, then the attribute spacecraft_clock_partition must be used.
- PDS4 data type: ASCII_Short_String_Collapsed
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Formation rule: [p/]dddddddddd[.fffffffff] - The spacecraft clock value is an integer with no more than 10 digits, optionally preceded by a clock partition number and forward slash, and optionally followed by a fractional value. If the fractional value is present, it must be separated from the whole number by a period, and may have up to 9 digits. If a partition number and slash are not present, then the attribute spacecraft_clock_partition must be used.
- Minimum characters: 1
- Maximum characters: 19
- Pattern: ([1-9]/)?[0-9]{1,10}(\.[0-9]{1,9})?

*start_local_true_solar_time*
Start_local_true_solar_time is the local true solar time, as defined in the main PDS4 data dictionary, at the beginning of an observation.
- PDS4 data type: ASCII_Short_String_Collapsed
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Formation rule: [[Sol-]nnnnn ]hh:mm:ss[.fffff] - Local true solar time is given in hours, minutes and seconds, optionally followed by a decimal point and fractional seconds. The time may be preceded by "nnnnn " or "Sol-nnnnn " where nnnnn is the sol number, separated from the time by a space character. If no sol number is present, the attribute start_local_true_solar_time_sol should be used to specify the sol number.
- Minimum characters: 8
- Maximum characters: 24
- Pattern: ((Sol\-)?[0-9]{1,5} )?[0-2][0-9]:[0-5][0-9]:[0-5][0-9](\.[0-9]{1,5})?

*start_local_true_solar_time_sol*
The start_local_true_solar_time_sol element specifies the number of solar days elapsed since a reference day (e.g. the day on which a landing vehicle set down) for local true solar time (LTST). Days are measured in rotations of the planet in question from midnight to midnight. The reference day is '0', as Landing day is Sol 0. If before Landing day, then value will be less than or equal to '0' and can be negative. Start_local_true_solar_time_sol should accompany the attribute start_local_true_solar_time if that attribute's value does not include a sol number prefix.
- PDS4 data type: ASCII_Integer
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 0

*stop_local_true_solar_time*
Stop_local_true_solar_time is the local true solar time, as defined in the main PDS4 data dictionary, at the end of an observation.
- PDS4 data type: ASCII_Short_String_Collapsed
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Formation rule: [[Sol-]nnnnn ]hh:mm:ss[.fffff] - Local true solar time is given in hours, minutes and seconds, optionally followed by a decimal point and fractional seconds. The time may be preceded by "nnnnn " or "Sol-nnnnn " where nnnnn is the sol number, separated from the time by a space character. If no sol number is present, the attribute stop_local_true_solar_time_sol should be used to specify the sol number.
- Minimum characters: 8
- Maximum characters: 24
- Pattern: ((Sol\-)?[0-9]{1,5} )?[0-2][0-9]:[0-5][0-9]:[0-5][0-9](\.[0-9]{1,5})?

*stop_local_true_solar_time_sol*
The stop_local_true_solar_time_sol element specifies the number of solar days elapsed since a reference day (e.g. the day on which a landing vehicle set down) for local true solar time (LTST). Days are measured in rotations of the planet in question from midnight to midnight. The reference day is '0', as Landing day is Sol 0. If before Landing day, then value will be less than or equal to '0' and can be negative. Stop_local_true_solar_time_sol should accompany the attribute stop_local_true_solar_time if that attribute's value does not include a sol number prefix.
- PDS4 data type: ASCII_Integer
- Minimum occurrences: 0
- Maximum occurrences: 1
- Nillable: No
- Minimum value: 0


# Examples

Example PDS4 label snippet for MSL APXS raw data product:

```
       <Mission_Area>
        <msl:MSL_Parameters>
          <msl:Observation_Information>
            <msl:release_number>0011</msl:release_number>
            <msl:product_type>APXS_EDR</msl:product_type>
            <msl:mission_phase_name>EXTENDED SURFACE MISSION</msl:mission_phase_name>
            <msl:spacecraft_clock_start>0397764256.344</msl:spacecraft_clock_start>
            <msl:spacecraft_clock_stop>0397764725.402</msl:spacecraft_clock_stop>
            <msl:spacecraft_clock_partition>1</msl:spacecraft_clock_partition>
            <msl:sol_number>3</msl:sol_number>
            <msl:active_flight_computer>A</msl:active_flight_computer>
            <msl:producer_institution_name>Multimission Image Processing Subsystem, Jet Propulsion Lab</msl:producer_institution_name>
          </msl:Observation_Information>
        </msl:MSL_Parameters>
       </Mission_Area>
``` 
