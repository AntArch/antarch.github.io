---
Date: 2014-01-16 15:15
Title: DART meeting with Keith Wilkinson about research
Category: DART, meeting, research, analysis
Tags: DART, meeting, analysis, postgres, python, statistics
layout: post
---

Taken from a mindmap

#Aim
* To understand the gaps between sensor reqponses, environmental variables and soil measurements
* Discuss building up the stats back end model
#Topics
* CMD mini explorer
    * In theory measures resistivity and mag
    * Can compare this with the mag sus samples whjch were used as control
    * We would need to look at this
    * The theory is
        * The mag sus element of the ERT reading should not change
            * We have a control already
        * This means that we should be able to identify the conductivity variations as the seond component
            * These should be comparable to Dans data
        * THIS ALL NEEDS FUSING
* Publication holes
    * Morphological description from the sections
        * Grain size and organics
        * Geo-archaeology
        * Journal of field archaeology
        * This should become a position paper for a follow on grant
    * Correlation of the magnetometry surveys
        * Breakdown assumptions that measurements are down to 1m
        * We have this in diddington
    * Comparison of
        * Grain size
        * Magnetics
        * Compare mag variations in clay rich components both on and off site
            * This would need correction of organic
        * Get measurements from the same spatial location and undertake multivariate analysis
        * Understand 'natural' and then see how anthropogenic variations
        * If aggregation is required then we can average
        * Remember things can be very heavily skewed if ceramic fragments in the sample
            * Outliers may need removing
    * Comparison of archaeological and engineering soils
        * Unfortunately Birmingham undertake data aggregation before they publish
        * Need to get access to the underlying RAW data from Birmingham
        * Note: there is a difference between raw data and presentation synthesis
            * Birmingham want to synthesise data
    * Arrange a meeting with Chris G and ArminS when initial stats framework in place
* David Jordan
    * Throwing a whole load of techniques aimed at percolation modelling to see what sticks
* Project proposal
    * Permanent monitoring
        * Install permanent ERT sensor
            * Monitor for 14 months
            * £30k?
        * Excavate section
            * £3k
        * Record section
            * SfM
            * Multiple interpretations
            * write archaeological contractors into the project design to get this done as contribution in kind
                * Leave the hole open for a period of days
                * Allow the section to be cut back (if necessary)
            * include contexts
        * Take high resolution in-situ mag-sus (2-5)cm intervals)
            * £0k
        * Sample at very high resolution
            * £0.5k
        * Run analysis on monoliths
            * Particle size
            * Mag Sus
            * Organic content
            * £40k
        * Build section based on lab analyses
        * Publish
            * accuracy of the section and context recording
            * What degree of granularity required to capture full sequence 

#Things to do
* ARB
    * Start building up comparisons between recorded soil properties and lab soil properties
    * Matching the quantitative lab measurements to the qualitiative field descriptions
* Keith
    * See about picking up some samples for Cherry Copse ditch
* Chris/Rob
    * Host the Bartington magnetometry data
* Harnhill chery copse data
    * The reported profile in the lab measurements is wrong
    * They are reported as butting
    * However, on the section drawings they overlap
    * I think this is fixed in the data model
        * Check
