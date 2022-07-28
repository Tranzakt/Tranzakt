# tranzakt

Tranzakt is (for the moment at least) a Proof of Concept for a new web database application tool.

Inspired by Fabrik, a Joomla extension, Tranzakt is intended to provide:

* A web-based development environment for web-based SQL-based data applications
* A stand-alone run-time environment that is intended to be run either:
  * stand-alone; or
  * interfaced with main web sites based on CMSes like Joomla running in a separate webserver instance.

## Target Functionality

* Lists (tabular presentation of data - like rows in a table)
* Forms (a single database record - possibly with sub-rows)
* Visualisers (graphs or any other way of visualising data)
* Themes - a replaceable set of element components to fit with a joomla template design or to giove an alternative visual style
* A range of data-field types (limited scope for the proof of concept)
* A debugging log (issued to the JS console) showing key execution details - global summary switch, specific element detail switch.
* Synchronous and asynchronous API (only synchronous will be delivered in the PoC)
* Stand-alone operation
* Integration with CMS' such as Joomla (inc. integration with the CMS security) (not part of proof of concept which will be entirely stand-alone)

It is intended that any final product will be delivered with:

* Both run-time and development versions
* Internal documentation (provided using code comments)
* User documentation (provided as help web pages delivered with the development version
* Automated regression tests (to confirm functionality as seen by the user)
* Automated unit tests (to confirm internal functionality esp. boundary cases)
* Internationalisation (UK english will be default language)
* A clever caching system to improve performance - key needs are for caching to
understand and respect security context and for cache entries to be invalidated as needed.
To achieve this the cache naming/hashing needs to be carefully designed to
e.g. invalidate all copies of data that has changed regardless of security context.
* A versioning system (to take a snapshot of a developed system and export it as a self-contained package)
* An SQL upgrade system (to make the schema / data changes to update an older version to a newer version)

It is not anticipated that much (if any) of the above  will be delivered as part of the PoC.

## Design principles

* RESTful principles
* Design by Contract (another way of ensuring code quality by tightly defining and policing interfaces)
* Carefully architected small objects (because small objects are more maintainable and extensible)
* Focus on core kernel (as a great kernel and excellent abstraction will make delivery of the range of functionality much easier)

## Technology

This PoC is intended to be based on PHP for the server environment.
If this turns out to be lacking in functionality, then a second attempt may be made using Python.

The reasons for delivering the run-time environment in a separate webserver instance are:

* To decouple the Tranzakt code from the CMS code,
reducing the codependencies to an absolute minimum and minimising the impact of CMS changes
(e.g. those created by Joomla 2->3 and 3->4) on the Tranzakt codebase.
Additionally by doing this we enable the same code-base to be interfaced with several different CMSes
(e.g. Joomla and Wordpress) broadening the user base and making the ongoing maintenance more viable.
* To enable it to take advantage of leading server and client frameworks that will
massively simplify the amount of code that needs to be written,
but which would likely be incompatible with the CMS.
* To enable the Tranzakt code to run in parallel with the CMS web page generation code
* To enable it to use asynchronous and multi-tasking techniques to improve performance and response times

The first attempt at a Proof of Concept will be based on the following other open-source technologies:

* Laravel, which is itself based on...
* Symfony (a lower level framework)
* Eloquent (an Object Relational Mapper)
* React.js
* Vue.js

As development proceeds, we will likely add more technologies.

## Contributions

Contributions are welcome from anyone wishing to help develop the PoC. Please submit PRs.

A pre-configured development environment for Windows is delivered
in [Tranzakt-dev-laragon-win64](https://github.com/Tranzakt/Tranzakt-dev-laragon-win64).

# Copyright & License

The Tranzakt software is Copyright (C) 2022 Tranzakt

This library is free software; you can redistribute it and/or
modify it under the terms of the GNU Lesser General Public
License as published by the Free Software Foundation; either
version 2.1 of the License, or (at your option) any later version.

This library is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
Lesser General Public License for more details.

You should have received a copy of the GNU Lesser General Public
License along with this library; if not, write to the Free Software
Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301
USA
