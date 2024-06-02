---
aliases: [pydantic]
tags: [developer-tools, python, documentation]
---

# Pydantic

## Description

Data validation using Python type hints

## README

# Pydantic

[![CI](https://img.shields.io/github/actions/workflow/status/pydantic/pydantic/ci.yml?branch=main&logo=github&label=CI)](https://github.com/pydantic/pydantic/actions?query=event%3Apush+branch%3Amain+workflow%3ACI)
[![Coverage](https://coverage-badge.samuelcolvin.workers.dev/pydantic/pydantic.svg)](https://coverage-badge.samuelcolvin.workers.dev/redirect/pydantic/pydantic)
[![pypi](https://img.shields.io/pypi/v/pydantic.svg)](https://pypi.python.org/pypi/pydantic)
[![CondaForge](https://img.shields.io/conda/v/conda-forge/pydantic.svg)](https://anaconda.org/conda-forge/pydantic)
[![downloads](https://static.pepy.tech/badge/pydantic/month)](https://pepy.tech/project/pydantic)
[![versions](https://img.shields.io/pypi/pyversions/pydantic.svg)](https://github.com/pydantic/pydantic)
[![license](https://img.shields.io/github/license/pydantic/pydantic.svg)](https://github.com/pydantic/pydantic/blob/main/LICENSE)
[![Pydantic v2](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/pydantic/pydantic/main/docs/badge/v2.json)](https://docs.pydantic.dev/latest/contributing/#badges)

Data validation using Python type hints.

Fast and extensible, Pydantic plays nicely with your linters/IDE/brain.
Define how data should be in pure, canonical Python 3.8+; validate it with Pydantic.

## Pydantic Company :rocket

We've started a company based on the principles that I believe have led to Pydantic's success.
Learn more from the [Company Announcement](https://blog.pydantic.dev/blog/2023/02/16/company-announcement--pydantic/).

## Pydantic V1.10 vs. V2

Pydantic V2 is a ground-up rewrite that offers many new features, performance improvements, and some breaking changes compared to Pydantic V1.

If you're using Pydantic V1 you may want to look at the
[pydantic V1.10 Documentation](https://docs.pydantic.dev/) or,
[`1.10.X-fixes` git branch](https://github.com/pydantic/pydantic/tree/1.10.X-fixes). Pydantic V2 also ships with the latest version of Pydantic V1 built in so that you can incrementally upgrade your code base and projects: `from pydantic import v1 as pydantic_v1`.

## Help

See [documentation](https://docs.pydantic.dev/) for more details.

## Installation

Install using `pip install -U pydantic` or `conda install pydantic -c conda-forge`.
For more installation options to make Pydantic even faster,
see the [Install](https://docs.pydantic.dev/install/) section in the documentation.

## A Simple Example

```py
from datetime import datetime
from typing import List, Optional
from pydantic import BaseModel

class User(BaseModel):
    id: int
    name: str = 'John Doe'
    signup_ts: Optional[datetime] = None
    friends: List[int] = []

external_data = {'id': '123', 'signup_ts': '2017-06-01 12:22', 'friends': [1, '2', b'3']}
user = User(**external_data)
print(user)
#> User id=123 name='John Doe' signup_ts=datetime.datetime(2017, 6, 1, 12, 22) friends=[1, 2, 3]
print(user.id)
#> 123
```

## Contributing

For guidance on setting up a development environment and how to make a
contribution to Pydantic, see
[Contributing to Pydantic](https://docs.pydantic.dev/contributing/).

## Reporting a Security Vulnerability

See our [security policy](https://github.com/pydantic/pydantic/security/policy).

## Changelog

## V2.7.2 (2024-05-28)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.7.2)

### What's Changed

#### Packaging

* Bump `pydantic-core` to `v2.18.3` by [@sydney-runkle](https://github.com/sydney-runkle) in [#9515](https://github.com/pydantic/pydantic/pull/9515)

#### Fixes

* Replace `__spec__.parent` with `__package__` by [@hramezani](https://github.com/hramezani) in [#9331](https://github.com/pydantic/pydantic/pull/9331)
* Fix validation of `int`s with leading unary minus by [@RajatRajdeep](https://github.com/RajatRajdeep) in [pydantic/pydantic-core#1291](https://github.com/pydantic/pydantic-core/pull/1291)
* Fix `str` subclass validation for enums by [@sydney-runkle](https://github.com/sydney-runkle) in [pydantic/pydantic-core#1273]https://github.com/pydantic/pydantic-core/pull/1273
* Support `BigInt`s in `Literal`s and `Enum`s by [@samuelcolvin](https://github.com/samuelcolvin) in [pydantic/pydantic-core#1297]https://github.com/pydantic/pydantic-core/pull/1297
* Fix: uuid - allow `str` subclass as input by [@davidhewitt](https://github.com/davidhewitt) in [pydantic/pydantic-core#1296]https://github.com/pydantic/pydantic-core/pull/1296

## V2.7.1 (2024-04-23)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.7.1)

### What's Changed

#### Packaging

* Bump `pydantic-core` to `v2.18.3` by [@sydney-runkle](https://github.com/sydney-runkle) in [#9307](https://github.com/pydantic/pydantic/pull/9307)

#### New Features

* Ftp and Websocket connection strings support by [@CherrySuryp](https://github.com/CherrySuryp) in [#9205](https://github.com/pydantic/pydantic/pull/9205)

#### Changes

* Use field description for RootModel schema description when there is `…` by [@LouisGobert](https://github.com/LouisGobert) in [#9214](https://github.com/pydantic/pydantic/pull/9214)

#### Fixes

* Fix `validation_alias` behavior with `model_construct` for `AliasChoices` and `AliasPath` by [@sydney-runkle](https://github.com/sydney-runkle) in [#9223](https://github.com/pydantic/pydantic/pull/9223)
* Revert `typing.Literal` and import it outside the TYPE_CHECKING block by [@frost-nzcr4](https://github.com/frost-nzcr4) in [#9232](https://github.com/pydantic/pydantic/pull/9232)
* Fix `Secret` serialization schema, applicable for unions by [@sydney-runkle](https://github.com/sydney-runkle) in [#9240](https://github.com/pydantic/pydantic/pull/9240)
* Fix `strict` application to `function-after` with `use_enum_values` by [@sydney-runkle](https://github.com/sydney-runkle) in [#9279](https://github.com/pydantic/pydantic/pull/9279)
* Address case where `model_construct` on a class which defines `model_post_init` fails with `AttributeError` by [@babygrimes](https://github.com/babygrimes) in [#9168](https://github.com/pydantic/pydantic/pull/9168)
* Fix `model_json_schema` with config types by [@NeevCohen](https://github.com/NeevCohen) in [#9287](https://github.com/pydantic/pydantic/pull/9287)
* Support multiple zeros as an `int` by [@samuelcolvin](https://github.com/samuelcolvin) in [pydantic/pydantic-core#1269](https://github.com/pydantic/pydantic-core/pull/1269)
* Fix validation of `int`s with leading unary plus by [@cknv](https://github.com/cknv) in [pydantic/pydantic-core#1272](https://github.com/pydantic/pydantic-core/pull/1272)
* Fix interaction between `extra != 'ignore'` and `from_attributes=True` by [@davidhewitt](https://github.com/davidhewitt) in [pydantic/pydantic-core#1276](https://github.com/pydantic/pydantic-core/pull/1276)
* Handle error from `Enum`'s `missing` function as `ValidationError` by [@sydney-runkle](https://github.com/sydney-runkle) in [pydantic/pydantic-core#1274](https://github.com/pydantic/pydantic-core/pull/1754)
* Fix memory leak with `Iterable` validation by [@davidhewitt](https://github.com/davidhewitt) in [pydantic/pydantic-core#1271](https://github.com/pydantic/pydantic-core/pull/1751)

### New Contributors

* [@zzstoatzz](https://github.com/zzstoatzz) made their first contribution in [#9219](https://github.com/pydantic/pydantic/pull/9219)
* [@frost-nzcr4](https://github.com/frost-nzcr4) made their first contribution in [#9232](https://github.com/pydantic/pydantic/pull/9232)
* [@CherrySuryp](https://github.com/CherrySuryp) made their first contribution in [#9205](https://github.com/pydantic/pydantic/pull/9205)
* [@vagenas](https://github.com/vagenas) made their first contribution in [#9268](https://github.com/pydantic/pydantic/pull/9268)
* [@ollz272](https://github.com/ollz272) made their first contribution in [#9262](https://github.com/pydantic/pydantic/pull/9262)
* [@babygrimes](https://github.com/babygrimes) made their first contribution in [#9168](https://github.com/pydantic/pydantic/pull/9168)
* [@swelborn](https://github.com/swelborn) made their first contribution in [#9296](https://github.com/pydantic/pydantic/pull/9296)
* [@kf-novi](https://github.com/kf-novi) made their first contribution in [#9236](https://github.com/pydantic/pydantic/pull/9236)
* [@lgeiger](https://github.com/lgeiger) made their first contribution in [#9288](https://github.com/pydantic/pydantic/pull/9288)

## V2.7.0 (2024-04-11)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.7.0)

The code released in v2.7.0 is practically identical to that of v2.7.0b1.

### What's Changed

#### Packaging

* Reorganize `pyproject.toml` sections by [@Viicos](https://github.com/Viicos) in [#8899](https://github.com/pydantic/pydantic/pull/8899)
* Bump `pydantic-core` to `v2.18.1` by [@sydney-runkle](https://github.com/sydney-runkle) in [#9211](https://github.com/pydantic/pydantic/pull/9211)
* Adopt `jiter` `v0.2.0` by [@samuelcolvin](https://github.com/samuelcolvin) in [pydantic/pydantic-core#1250](https://github.com/pydantic/pydantic-core/pull/1250)

#### New Features

* Extract attribute docstrings from `FieldInfo.description` by [@Viicos](https://github.com/Viicos) in [#6563](https://github.com/pydantic/pydantic/pull/6563)
* Add a `with_config` decorator to comply with typing spec by [@Viicos](https://github.com/Viicos) in [#8611](https://github.com/pydantic/pydantic/pull/8611)
* Allow an optional separator splitting the value and unit of the result of `ByteSize.human_readable` by [@jks15satoshi](https://github.com/jks15satoshi) in [#8706](https://github.com/pydantic/pydantic/pull/8706)
* Add generic `Secret` base type by [@conradogarciaberrotaran](https://github.com/conradogarciaberrotaran) in [#8519](https://github.com/pydantic/pydantic/pull/8519)
* Make use of `Sphinx` inventories for cross references in docs by [@Viicos](https://github.com/Viicos) in [#8682](https://github.com/pydantic/pydantic/pull/8682)
* Add environment variable to disable plugins by [@geospackle](https://github.com/geospackle) in [#8767](https://github.com/pydantic/pydantic/pull/8767)
* Add support for `deprecated` fields by [@Viicos](https://github.com/Viicos) in [#8237](https://github.com/pydantic/pydantic/pull/8237)
* Allow `field_serializer('*')` by [@ornariece](https://github.com/ornariece) in [#9001](https://github.com/pydantic/pydantic/pull/9001)
* Handle a case when `model_config` is defined as a model property by [@alexeyt101](https://github.com/alexeyt101) in [#9004](https://github.com/pydantic/pydantic/pull/9004)
* Update `create_model()` to support `typing.Annotated` as input by [@wannieman98](https://github.com/wannieman98) in [#8947](https://github.com/pydantic/pydantic/pull/8947)
* Add `ClickhouseDsn` support by [@solidguy7](https://github.com/solidguy7) in [#9062](https://github.com/pydantic/pydantic/pull/9062)
* Add support for `re.Pattern[str]` to `pattern` field by [@jag-k](https://github.com/jag-k) in [#9053](https://github.com/pydantic/pydantic/pull/9053)
* Support for `serialize_as_any` runtime setting by [@sydney-runkle](https://github.com/sydney-runkle) in [#8830](https://github.com/pydantic/pydantic/pull/8830)
* Add support for `typing.Self` by [@Youssefares](https://github.com/Youssefares) in [#9023](https://github.com/pydantic/pydantic/pull/9023)
* Ability to pass `context` to serialization by [@ornariece](https://github.com/ornariece) in [#8965](https://github.com/pydantic/pydantic/pull/8965)
* Add feedback widget to docs with flarelytics integration by [@sydney-runkle](https://github.com/sydney-runkle) in [#9129](https://github.com/pydantic/pydantic/pull/9129)
* Support for parsing partial JSON strings in Python by [@samuelcolvin](https://github.com/samuelcolvin) in [pydantic/jiter#66](https://github.com/pydantic/jiter/pull/66)

**Finalized in v2.7.0, rather than v2.7.0b1:**
* Add support for field level number to str coercion option by [@NeevCohen](https://github.com/NeevCohen) in [#9137](https://github.com/pydantic/pydantic/pull/9137)
* Update `warnings` parameter for serialization utilities to allow raising a warning by [@Lance-Drane](https://github.com/Lance-Drane) in [#9166](https://github.com/pydantic/pydantic/pull/9166)

#### Changes

* Correct docs, logic for `model_construct` behavior with `extra` by [@sydney-runkle](https://github.com/sydney-runkle) in [#8807](https://github.com/pydantic/pydantic/pull/8807)
* Improve error message for improper `RootModel` subclasses by [@sydney-runkle](https://github.com/sydney-runkle) in [#8857](https://github.com/pydantic/pydantic/pull/8857)
* Use `PEP570` syntax by [@Viicos](https://github.com/Viicos) in [#8940](https://github.com/pydantic/pydantic/pull/8940)
* Add `enum` and `type` to the JSON schema for single item literals by [@dmontagu](https://github.com/dmontagu) in [#8944](https://github.com/pydantic/pydantic/pull/8944)
* Deprecate `update_json_schema` internal function by [@sydney-runkle](https://github.com/sydney-runkle) in [#9125](https://github.com/pydantic/pydantic/pull/9125)
* Serialize duration to hour minute second, instead of just seconds by [@kakilangit](https://github.com/kakilangit) in [pydantic/speedate#50](https://github.com/pydantic/speedate/pull/50)
* Trimming str before parsing to int and float by [@hungtsetse](https://github.com/hungtsetse) in [pydantic/pydantic-core#1203](https://github.com/pydantic/pydantic-core/pull/1203)

#### Performance

* `enum` validator improvements by [@samuelcolvin](https://github.com/samuelcolvin) in [#9045](https://github.com/pydantic/pydantic/pull/9045)
* Move `enum` validation and serialization to Rust by [@samuelcolvin](https://github.com/samuelcolvin) in [#9064](https://github.com/pydantic/pydantic/pull/9064)
* Improve schema generation for nested dataclasses by [@sydney-runkle](https://github.com/sydney-runkle) in [#9114](https://github.com/pydantic/pydantic/pull/9114)
* Fast path for ASCII python string creation in JSON by [@samuelcolvin](https://github.com/samuelcolvin) in in [pydantic/jiter#72](https://github.com/pydantic/jiter/pull/72)
* SIMD integer and string JSON parsing on `aarch64`(**Note:** SIMD on x86 will be implemented in a future release) by [@samuelcolvin](https://github.com/samuelcolvin) in in [pydantic/jiter#65](https://github.com/pydantic/jiter/pull/65)
* Support JSON `Cow<str>` from `jiter` by [@davidhewitt](https://github.com/davidhewitt) in [pydantic/pydantic-core#1231](https://github.com/pydantic/pydantic-core/pull/1231)
* MAJOR performance improvement: update to PyO3 0.21 final by [@davidhewitt](https://github.com/davidhewitt) in [pydantic/pydantic-core#1248](https://github.com/pydantic/pydantic-core/pull/1248)
* cache Python strings by [@samuelcolvin](https://github.com/samuelcolvin) in [pydantic/pydantic-core#1240](https://github.com/pydantic/pydantic-core/pull/1240)

#### Fixes

* Fix strict parsing for some `Sequence`s by [@sydney-runkle](https://github.com/sydney-runkle) in [#8614](https://github.com/pydantic/pydantic/pull/8614)
* Add a check on the existence of `__qualname__` by [@anci3ntr0ck](https://github.com/anci3ntr0ck) in [#8642](https://github.com/pydantic/pydantic/pull/8642)
* Handle `__pydantic_extra__` annotation being a string or inherited by [@alexmojaki](https://github.com/alexmojaki) in [#8659](https://github.com/pydantic/pydantic/pull/8659)
* Fix json validation for `NameEmail` by [@Holi0317](https://github.com/Holi0317) in [#8650](https://github.com/pydantic/pydantic/pull/8650)
* Fix type-safety of attribute access in `BaseModel` by [@bluenote10](https://github.com/bluenote10) in [#8651](https://github.com/pydantic/pydantic/pull/8651)
* Fix bug with `mypy` plugin and `no_strict_optional = True` by [@dmontagu](https://github.com/dmontagu) in [#8666](https://github.com/pydantic/pydantic/pull/8666)
* Fix `ByteSize` error `type` change by [@sydney-runkle](https://github.com/sydney-runkle) in [#8681](https://github.com/pydantic/pydantic/pull/8681)
* Fix inheriting annotations in dataclasses by [@sydney-runkle](https://github.com/sydney-runkle) in [#8679](https://github.com/pydantic/pydantic/pull/8679)
* Fix regression in core schema generation for indirect definition references by [@dmontagu](https://github.com/dmontagu) in [#8702](https://github.com/pydantic/pydantic/pull/8702)
* Fix unsupported types bug with plain validator by [@sydney-runkle](https://github.com/sydney-runkle) in [#8710](https://github.com/pydantic/pydantic/pull/8710)
* Reverting problematic fix from 2.6 release, fixing schema building bug by [@sydney-runkle](https://github.com/sydney-runkle) in [#8718](https://github.com/pydantic/pydantic/pull/8718)
* fixes `__pydantic_config__` ignored for TypeDict by [@13sin](https://github.com/13sin) in [#8734](https://github.com/pydantic/pydantic/pull/8734)
* Fix test failures with `pytest v8.0.0` due to `pytest.warns()` starting to work inside `pytest.raises()` by [@mgorny](https://github.com/mgorny) in [#8678](https://github.com/pydantic/pydantic/pull/8678)
* Use `is_valid_field` from 1.x for `mypy` plugin by [@DanielNoord](https://github.com/DanielNoord) in [#8738](https://github.com/pydantic/pydantic/pull/8738)
* Better-support `mypy` strict equality flag by [@dmontagu](https://github.com/dmontagu) in [#8799](https://github.com/pydantic/pydantic/pull/8799)
* model_json_schema export with Annotated types misses 'required' parameters by [@LouisGobert](https://github.com/LouisGobert) in [#8793](https://github.com/pydantic/pydantic/pull/8793)
* Fix default inclusion in `FieldInfo.__repr_args__` by [@sydney-runkle](https://github.com/sydney-runkle) in [#8801](https://github.com/pydantic/pydantic/pull/8801)
* Fix resolution of forward refs in dataclass base classes that are not present in the subclass module namespace by [@matsjoyce-refeyn](https://github.com/matsjoyce-refeyn) in [#8751](https://github.com/pydantic/pydantic/pull/8751)
* Fix `BaseModel` type annotations to be resolvable by `typing.get_type_hints` by [@devmonkey22](https://github.com/devmonkey22) in [#7680](https://github.com/pydantic/pydantic/pull/7680)
* Fix: allow empty string aliases with `AliasGenerator` by [@sydney-runkle](https://github.com/sydney-runkle) in [#8810](https://github.com/pydantic/pydantic/pull/8810)
* Fix test along with `date` -> `datetime` timezone assumption fix by [@sydney-runkle](https://github.com/sydney-runkle) in [#8823](https://github.com/pydantic/pydantic/pull/8823)
* Fix deprecation warning with usage of `ast.Str` by [@Viicos](https://github.com/Viicos) in [#8837](https://github.com/pydantic/pydantic/pull/8837)
* Add missing `deprecated` decorators by [@Viicos](https://github.com/Viicos) in [#8877](https://github.com/pydantic/pydantic/pull/8877)
* Fix serialization of `NameEmail` if name includes an email address by [@NeevCohen](https://github.com/NeevCohen) in [#8860](https://github.com/pydantic/pydantic/pull/8860)
* Add information about class in error message of schema generation by [@Czaki](https://github.com/Czaki) in [#8917](https://github.com/pydantic/pydantic/pull/8917)
* Make `TypeAdapter`'s typing compatible with special forms by [@adriangb](https://github.com/adriangb) in [#8923](https://github.com/pydantic/pydantic/pull/8923)
* Fix issue with config behavior being baked into the ref schema for `enum`s by [@dmontagu](https://github.com/dmontagu) in [#8920](https://github.com/pydantic/pydantic/pull/8920)
* More helpful error re wrong `model_json_schema` usage by [@sydney-runkle](https://github.com/sydney-runkle) in [#8928](https://github.com/pydantic/pydantic/pull/8928)
* Fix nested discriminated union schema gen, pt 2 by [@sydney-runkle](https://github.com/sydney-runkle) in [#8932](https://github.com/pydantic/pydantic/pull/8932)
* Fix schema build for nested dataclasses / TypedDicts with discriminators by [@sydney-runkle](https://github.com/sydney-runkle) in [#8950](https://github.com/pydantic/pydantic/pull/8950)
* Remove unnecessary logic for definitions schema gen with discriminated unions by [@sydney-runkle](https://github.com/sydney-runkle) in [#8951](https://github.com/pydantic/pydantic/pull/8951)
* Fix handling of optionals in `mypy` plugin by [@dmontagu](https://github.com/dmontagu) in [#9008](https://github.com/pydantic/pydantic/pull/9008)
* Fix `PlainSerializer` usage with std type constructor by [@sydney-runkle](https://github.com/sydney-runkle) in [#9031](https://github.com/pydantic/pydantic/pull/9031)
* Remove unnecessary warning for config in plugin by [@dmontagu](https://github.com/dmontagu) in [#9039](https://github.com/pydantic/pydantic/pull/9039)
* Fix default value serializing by [@NeevCohen](https://github.com/NeevCohen) in [#9066](https://github.com/pydantic/pydantic/pull/9066)
* Fix extra fields check in `Model.__getattr__()` by [@NeevCohen](https://github.com/NeevCohen) in [#9082](https://github.com/pydantic/pydantic/pull/9082)
* Fix `ClassVar` forward ref inherited from parent class by [@alexmojaki](https://github.com/alexmojaki) in [#9097](https://github.com/pydantic/pydantic/pull/9097)
* fix sequence like validator with strict `True` by [@andresliszt](https://github.com/andresliszt) in [#8977](https://github.com/pydantic/pydantic/pull/8977)
* Improve warning message when a field name shadows a field in a parent model by [@chan-vince](https://github.com/chan-vince) in [#9105](https://github.com/pydantic/pydantic/pull/9105)
* Do not warn about shadowed fields if they are not redefined in a child class by [@chan-vince](https://github.com/chan-vince) in [#9111](https://github.com/pydantic/pydantic/pull/9111)
* Fix discriminated union bug with unsubstituted type var by [@sydney-runkle](https://github.com/sydney-runkle) in [#9124](https://github.com/pydantic/pydantic/pull/9124)
* Support serialization of `deque` when passed to `Sequence[blah blah blah]` by [@sydney-runkle](https://github.com/sydney-runkle) in [#9128](https://github.com/pydantic/pydantic/pull/9128)
* Init private attributes from super-types in `model_post_init` by [@Viicos](https://github.com/Viicos) in [#9134](https://github.com/pydantic/pydantic/pull/9134)
* fix `model_construct` with `validation_alias` by [@ornariece](https://github.com/ornariece) in [#9144](https://github.com/pydantic/pydantic/pull/9144)
* Ensure json-schema generator handles `Literal` `null` types by [@bruno-f-cruz](https://github.com/bruno-f-cruz) in [#9135](https://github.com/pydantic/pydantic/pull/9135)
* **Fixed in v2.7.0**: Fix allow extra generic by [@dmontagu](https://github.com/dmontagu) in [#9193](https://github.com/pydantic/pydantic/pull/9193)

### New Contributors

* [@hungtsetse](https://github.com/hungtsetse) made their first contribution in [#8546](https://github.com/pydantic/pydantic/pull/8546)
* [@StrawHatDrag0n](https://github.com/StrawHatDrag0n) made their first contribution in [#8583](https://github.com/pydantic/pydantic/pull/8583)
* [@anci3ntr0ck](https://github.com/anci3ntr0ck) made their first contribution in [#8642](https://github.com/pydantic/pydantic/pull/8642)
* [@Holi0317](https://github.com/Holi0317) made their first contribution in [#8650](https://github.com/pydantic/pydantic/pull/8650)
* [@bluenote10](https://github.com/bluenote10) made their first contribution in [#8651](https://github.com/pydantic/pydantic/pull/8651)
* [@ADSteele916](https://github.com/ADSteele916) made their first contribution in [#8703](https://github.com/pydantic/pydantic/pull/8703)
* [@musicinmybrain](https://github.com/musicinmybrain) made their first contribution in [#8731](https://github.com/pydantic/pydantic/pull/8731)
* [@jks15satoshi](https://github.com/jks15satoshi) made their first contribution in [#8706](https://github.com/pydantic/pydantic/pull/8706)
* [@13sin](https://github.com/13sin) made their first contribution in [#8734](https://github.com/pydantic/pydantic/pull/8734)
* [@DanielNoord](https://github.com/DanielNoord) made their first contribution in [#8738](https://github.com/pydantic/pydantic/pull/8738)
* [@conradogarciaberrotaran](https://github.com/conradogarciaberrotaran) made their first contribution in [#8519](https://github.com/pydantic/pydantic/pull/8519)
* [@chris-griffin](https://github.com/chris-griffin) made their first contribution in [#8775](https://github.com/pydantic/pydantic/pull/8775)
* [@LouisGobert](https://github.com/LouisGobert) made their first contribution in [#8793](https://github.com/pydantic/pydantic/pull/8793)
* [@matsjoyce-refeyn](https://github.com/matsjoyce-refeyn) made their first contribution in [#8751](https://github.com/pydantic/pydantic/pull/8751)
* [@devmonkey22](https://github.com/devmonkey22) made their first contribution in [#7680](https://github.com/pydantic/pydantic/pull/7680)
* [@adamency](https://github.com/adamency) made their first contribution in [#8847](https://github.com/pydantic/pydantic/pull/8847)
* [@MamfTheKramf](https://github.com/MamfTheKramf) made their first contribution in [#8851](https://github.com/pydantic/pydantic/pull/8851)
* [@ornariece](https://github.com/ornariece) made their first contribution in [#9001](https://github.com/pydantic/pydantic/pull/9001)
* [@alexeyt101](https://github.com/alexeyt101) made their first contribution in [#9004](https://github.com/pydantic/pydantic/pull/9004)
* [@wannieman98](https://github.com/wannieman98) made their first contribution in [#8947](https://github.com/pydantic/pydantic/pull/8947)
* [@solidguy7](https://github.com/solidguy7) made their first contribution in [#9062](https://github.com/pydantic/pydantic/pull/9062)
* [@kloczek](https://github.com/kloczek) made their first contribution in [#9047](https://github.com/pydantic/pydantic/pull/9047)
* [@jag-k](https://github.com/jag-k) made their first contribution in [#9053](https://github.com/pydantic/pydantic/pull/9053)
* [@priya-gitTest](https://github.com/priya-gitTest) made their first contribution in [#9088](https://github.com/pydantic/pydantic/pull/9088)
* [@Youssefares](https://github.com/Youssefares) made their first contribution in [#9023](https://github.com/pydantic/pydantic/pull/9023)
* [@chan-vince](https://github.com/chan-vince) made their first contribution in [#9105](https://github.com/pydantic/pydantic/pull/9105)
* [@bruno-f-cruz](https://github.com/bruno-f-cruz) made their first contribution in [#9135](https://github.com/pydantic/pydantic/pull/9135)
* [@Lance-Drane](https://github.com/Lance-Drane) made their first contribution in [#9166](https://github.com/pydantic/pydantic/pull/9166)

## v2.7.0b1 (2024-04-03)

Pre-release, see [the GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.7.0b1) for details.

## V2.6.4 (2024-03-12)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.6.4)

### What's Changed

#### Fixes

* Fix usage of `AliasGenerator` with `computed_field` decorator by [@sydney-runkle](https://github.com/sydney-runkle) in [#8806](https://github.com/pydantic/pydantic/pull/8806)
* Fix nested discriminated union schema gen, pt 2 by [@sydney-runkle](https://github.com/sydney-runkle) in [#8932](https://github.com/pydantic/pydantic/pull/8932)
* Fix bug with no_strict_optional=True caused by API deferral by [@dmontagu](https://github.com/dmontagu) in [#8826](https://github.com/pydantic/pydantic/pull/8826)

## V2.6.3 (2024-02-27)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.6.3)

### What's Changed

#### Packaging

* Update `pydantic-settings` version in the docs by [@hramezani](https://github.com/hramezani) in [#8906](https://github.com/pydantic/pydantic/pull/8906)

#### Fixes

* Fix discriminated union schema gen bug by [@sydney-runkle](https://github.com/sydney-runkle) in [#8904](https://github.com/pydantic/pydantic/pull/8904)

## V2.6.2 (2024-02-23)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.6.2)

### What's Changed

#### Packaging

* Upgrade to `pydantic-core` 2.16.3 by [@sydney-runkle](https://github.com/sydney-runkle) in [#8879](https://github.com/pydantic/pydantic/pull/8879)

#### Fixes

* 'YYYY-MM-DD' date string coerced to datetime shouldn't infer timezone by [@sydney-runkle](https://github.com/sydney-runkle) in [pydantic/pydantic-core#1193](https://github.com/pydantic/pydantic-core/pull/1193)

## V2.6.1 (2024-02-05)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.6.1)

### What's Changed

#### Packaging

* Upgrade to `pydantic-core` 2.16.2 by [@sydney-runkle](https://github.com/sydney-runkle) in [#8717](https://github.com/pydantic/pydantic/pull/8717)

#### Fixes

* Fix bug with `mypy` plugin and `no_strict_optional = True` by [@dmontagu](https://github.com/dmontagu) in [#8666](https://github.com/pydantic/pydantic/pull/8666)
* Fix `ByteSize` error `type` change by [@sydney-runkle](https://github.com/sydney-runkle) in [#8681](https://github.com/pydantic/pydantic/pull/8681)
* Fix inheriting `Field` annotations in dataclasses by [@sydney-runkle](https://github.com/sydney-runkle) in [#8679](https://github.com/pydantic/pydantic/pull/8679)
* Fix regression in core schema generation for indirect definition references by [@dmontagu](https://github.com/dmontagu) in [#8702](https://github.com/pydantic/pydantic/pull/8702)
* Fix unsupported types bug with `PlainValidator` by [@sydney-runkle](https://github.com/sydney-runkle) in [#8710](https://github.com/pydantic/pydantic/pull/8710)
* Reverting problematic fix from 2.6 release, fixing schema building bug by [@sydney-runkle](https://github.com/sydney-runkle) in [#8718](https://github.com/pydantic/pydantic/pull/8718)
* Fix warning for tuple of wrong size in `Union` by [@davidhewitt](https://github.com/davidhewitt) in [pydantic/pydantic-core#1174](https://github.com/pydantic/pydantic-core/pull/1174)
* Fix `computed_field` JSON serializer `exclude_none` behavior by [@sydney-runkle](https://github.com/sydney-runkle) in [pydantic/pydantic-core#1187](https://github.com/pydantic/pydantic-core/pull/1187)

## V2.6.0 (2024-01-23)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.6.0)

The code released in v2.6.0 is practically identical to that of v2.6.0b1.

### What's Changed

#### Packaging

* Check for `email-validator` version >= 2.0 by [@commonism](https://github.com/commonism) in [#6033](https://github.com/pydantic/pydantic/pull/6033)
* Upgrade `ruff`` target version to Python 3.8 by [@Elkiwa](https://github.com/Elkiwa) in [#8341](https://github.com/pydantic/pydantic/pull/8341)
* Update to `pydantic-extra-types==2.4.1` by [@yezz123](https://github.com/yezz123) in [#8478](https://github.com/pydantic/pydantic/pull/8478)
* Update to `pyright==1.1.345` by [@Viicos](https://github.com/Viicos) in [#8453](https://github.com/pydantic/pydantic/pull/8453)
* Update pydantic-core from 2.14.6 to 2.16.1, significant changes from these updates are described below, full changelog [here](https://github.com/pydantic/pydantic-core/compare/v2.14.6...v2.16.1)

#### New Features

* Add `NatsDsn` by [@ekeew](https://github.com/ekeew) in [#6874](https://github.com/pydantic/pydantic/pull/6874)
* Add `ConfigDict.ser_json_inf_nan` by [@davidhewitt](https://github.com/davidhewitt) in [#8159](https://github.com/pydantic/pydantic/pull/8159)
* Add `types.OnErrorOmit` by [@adriangb](https://github.com/adriangb) in [#8222](https://github.com/pydantic/pydantic/pull/8222)
* Support `AliasGenerator` usage by [@sydney-runkle](https://github.com/sydney-runkle) in [#8282](https://github.com/pydantic/pydantic/pull/8282)
* Add Pydantic People Page to docs by [@sydney-runkle](https://github.com/sydney-runkle) in [#8345](https://github.com/pydantic/pydantic/pull/8345)
* Support `yyyy-MM-DD` datetime parsing by [@sydney-runkle](https://github.com/sydney-runkle) in [#8404](https://github.com/pydantic/pydantic/pull/8404)
* Added bits conversions to the `ByteSize` class [#8415](https://github.com/pydantic/pydantic/issues/8415) by [@luca-matei](https://github.com/luca-matei) in [#8507](https://github.com/pydantic/pydantic/pull/8507)
* Enable json schema creation with type `ByteSize` by [@geospackle](https://github.com/geospackle) in [#8537](https://github.com/pydantic/pydantic/pull/8537)
* Add `eval_type_backport` to handle union operator and builtin generic subscripting in older Pythons by [@alexmojaki](https://github.com/alexmojaki) in [#8209](https://github.com/pydantic/pydantic/pull/8209)
* Add support for `dataclass` fields `init` by [@dmontagu](https://github.com/dmontagu) in [#8552](https://github.com/pydantic/pydantic/pull/8552)
* Implement pickling for `ValidationError` by [@davidhewitt](https://github.com/davidhewitt) in [pydantic/pydantic-core#1119](https://github.com/pydantic/pydantic-core/pull/1119)
* Add unified tuple validator that can handle "variadic" tuples via PEP-646 by [@dmontagu](https://github.com/dmontagu) in [pydantic/pydantic-core#865](https://github.com/pydantic/pydantic-core/pull/865)

#### Changes

* Drop Python3.7 support by [@hramezani](https://github.com/hramezani) in [#7188](https://github.com/pydantic/pydantic/pull/7188)
* Drop Python 3.7, and PyPy 3.7 and 3.8 by [@davidhewitt](https://github.com/davidhewitt) in [pydantic/pydantic-core#1129](https://github.com/pydantic/pydantic-core/pull/1129)
* Use positional-only `self` in `BaseModel` constructor, so no field name can ever conflict with it by [@ariebovenberg](https://github.com/ariebovenberg) in [#8072](https://github.com/pydantic/pydantic/pull/8072)
* Make `@validate_call` return a function instead of a custom descriptor - fixes binding issue with inheritance and adds `self/cls` argument to validation errors by [@alexmojaki](https://github.com/alexmojaki) in [#8268](https://github.com/pydantic/pydantic/pull/8268)
* Exclude `BaseModel` docstring from JSON schema description by [@sydney-runkle](https://github.com/sydney-runkle) in [#8352](https://github.com/pydantic/pydantic/pull/8352)
* Introducing `classproperty` decorator for `model_computed_fields` by [@Jocelyn-Gas](https://github.com/Jocelyn-Gas) in [#8437](https://github.com/pydantic/pydantic/pull/8437)
* Explicitly raise an error if field names clashes with types by [@Viicos](https://github.com/Viicos) in [#8243](https://github.com/pydantic/pydantic/pull/8243)
* Use stricter serializer for unions of simple types by [@alexdrydew](https://github.com/alexdrydew) [pydantic/pydantic-core#1132](https://github.com/pydantic/pydantic-core/pull/1132)

#### Performance

* Add Codspeed profiling Actions workflow by [@lambertsbennett](https://github.com/lambertsbennett) in [#8054](https://github.com/pydantic/pydantic/pull/8054)
* Improve `int` extraction by [@samuelcolvin](https://github.com/samuelcolvin) in [pydantic/pydantic-core#1155](https://github.com/pydantic/pydantic-core/pull/1155)
* Improve performance of recursion guard by [@samuelcolvin](https://github.com/samuelcolvin) in [pydantic/pydantic-core#1156](https://github.com/pydantic/pydantic-core/pull/1156)
* `dataclass` serialization speedups by [@samuelcolvin](https://github.com/samuelcolvin) in [pydantic/pydantic-core#1162](https://github.com/pydantic/pydantic-core/pull/1162)
* Avoid `HashMap` creation when looking up small JSON objects in `LazyIndexMaps` by [@samuelcolvin](https://github.com/samuelcolvin) in [pydantic/jiter#55](https://github.com/pydantic/jiter/pull/55)
* use hashbrown to speedup python string caching by [@davidhewitt](https://github.com/davidhewitt) in [pydantic/jiter#51](https://github.com/pydantic/jiter/pull/51)
* Replace `Peak` with more efficient `Peek` by [@davidhewitt](https://github.com/davidhewitt) in [pydantic/jiter#48](https://github.com/pydantic/jiter/pull/48)

#### Fixes

* Move `getattr` warning in deprecated `BaseConfig` by [@tlambert03](https://github.com/tlambert03) in [#7183](https://github.com/pydantic/pydantic/pull/7183)
* Only hash `model_fields`, not whole `__dict__` by [@alexmojaki](https://github.com/alexmojaki) in [#7786](https://github.com/pydantic/pydantic/pull/7786)
* Fix mishandling of unions while freezing types in the `mypy` plugin by [@dmontagu](https://github.com/dmontagu) in [#7411](https://github.com/pydantic/pydantic/pull/7411)
* Fix `mypy` error on untyped `ClassVar` by [@vincent-hachin-wmx](https://github.com/vincent-hachin-wmx) in [#8138](https://github.com/pydantic/pydantic/pull/8138)
* Only compare pydantic fields in `BaseModel.__eq__` instead of whole `__dict__` by [@QuentinSoubeyranAqemia](https://github.com/QuentinSoubeyranAqemia) in [#7825](https://github.com/pydantic/pydantic/pull/7825)
* Update `strict` docstring in `model_validate` method. by [@LukeTonin](https://github.com/LukeTonin) in [#8223](https://github.com/pydantic/pydantic/pull/8223)
* Fix overload position of `computed_field` by [@Viicos](https://github.com/Viicos) in [#8227](https://github.com/pydantic/pydantic/pull/8227)
* Fix custom type type casting used in multiple attributes by [@ianhfc](https://github.com/ianhfc) in [#8066](https://github.com/pydantic/pydantic/pull/8066)
* Fix issue not allowing `validate_call` decorator to be dynamically assigned to a class method by [@jusexton](https://github.com/jusexton) in [#8249](https://github.com/pydantic/pydantic/pull/8249)
* Fix issue `unittest.mock` deprecation warnings by [@ibleedicare](https://github.com/ibleedicare) in [#8262](https://github.com/pydantic/pydantic/pull/8262)
* Added tests for the case `JsonValue` contains subclassed primitive values by [@jusexton](https://github.com/jusexton) in [#8286](https://github.com/pydantic/pydantic/pull/8286)
* Fix `mypy` error on free before validator (classmethod) by [@sydney-runkle](https://github.com/sydney-runkle) in [#8285](https://github.com/pydantic/pydantic/pull/8285)
* Fix `to_snake` conversion by [@jevins09](https://github.com/jevins09) in [#8316](https://github.com/pydantic/pydantic/pull/8316)
* Fix type annotation of `ModelMetaclass.__prepare__` by [@slanzmich](https://github.com/slanzmich) in [#8305](https://github.com/pydantic/pydantic/pull/8305)
* Disallow `config` specification when initializing a `TypeAdapter` when the annotated type has config already by [@sydney-runkle](https://github.com/sydney-runkle) in [#8365](https://github.com/pydantic/pydantic/pull/8365)
* Fix a naming issue with JSON schema for generics parametrized by recursive type aliases by [@dmontagu](https://github.com/dmontagu) in [#8389](https://github.com/pydantic/pydantic/pull/8389)
* Fix type annotation in pydantic people script by [@shenxiangzhuang](https://github.com/shenxiangzhuang) in [#8402](https://github.com/pydantic/pydantic/pull/8402)
* Add support for field `alias` in `dataclass` signature by [@NeevCohen](https://github.com/NeevCohen) in [#8387](https://github.com/pydantic/pydantic/pull/8387)
* Fix bug with schema generation with `Field(...)` in a forward ref by [@dmontagu](https://github.com/dmontagu) in [#8494](https://github.com/pydantic/pydantic/pull/8494)
* Fix ordering of keys in `__dict__` with `model_construct` call by [@sydney-runkle](https://github.com/sydney-runkle) in [#8500](https://github.com/pydantic/pydantic/pull/8500)
* Fix module `path_type` creation when globals does not contain `__name__` by [@hramezani](https://github.com/hramezani) in [#8470](https://github.com/pydantic/pydantic/pull/8470)
* Fix for namespace issue with dataclasses with `from __future__ import annotations` by [@sydney-runkle](https://github.com/sydney-runkle) in [#8513](https://github.com/pydantic/pydantic/pull/8513)
* Fix: make function validator types positional-only by [@pmmmwh](https://github.com/pmmmwh) in [#8479](https://github.com/pydantic/pydantic/pull/8479)
* Fix usage of `@deprecated` by [@Viicos](https://github.com/Viicos) in [#8294](https://github.com/pydantic/pydantic/pull/8294)
* Add more support for private attributes in `model_construct` call by [@sydney-runkle](https://github.com/sydney-runkle) in [#8525](https://github.com/pydantic/pydantic/pull/8525)
* Use a stack for the types namespace by [@dmontagu](https://github.com/dmontagu) in [#8378](https://github.com/pydantic/pydantic/pull/8378)
* Fix schema-building bug with `TypeAliasType` for types with refs by [@dmontagu](https://github.com/dmontagu) in [#8526](https://github.com/pydantic/pydantic/pull/8526)
* Support `pydantic.Field(repr=False)` in dataclasses by [@tigeryy2](https://github.com/tigeryy2) in [#8511](https://github.com/pydantic/pydantic/pull/8511)
* Override `dataclass_transform` behavior for `RootModel` by [@Viicos](https://github.com/Viicos) in [#8163](https://github.com/pydantic/pydantic/pull/8163)
* Refactor signature generation for simplicity by [@sydney-runkle](https://github.com/sydney-runkle) in [#8572](https://github.com/pydantic/pydantic/pull/8572)
* Fix ordering bug of PlainValidator annotation by [@Anvil](https://github.com/Anvil) in [#8567](https://github.com/pydantic/pydantic/pull/8567)
* Fix `exclude_none` for json serialization of `computed_field`s by [@sydney-runkle](https://github.com/sydney-runkle) in [pydantic/pydantic-core#1098](https://github.com/pydantic/pydantic-core/pull/1098)
* Support yyyy-MM-DD string for datetimes by [@sydney-runkle](https://github.com/sydney-runkle) in [pydantic/pydantic-core#1124](https://github.com/pydantic/pydantic-core/pull/1124)
* Tweak ordering of definitions in generated schemas by [@StrawHatDrag0n](https://github.com/StrawHatDrag0n) in [#8583](https://github.com/pydantic/pydantic/pull/8583)

### New Contributors

#### `pydantic`

* [@ekeew](https://github.com/ekeew) made their first contribution in [#6874](https://github.com/pydantic/pydantic/pull/6874)
* [@lambertsbennett](https://github.com/lambertsbennett) made their first contribution in [#8054](https://github.com/pydantic/pydantic/pull/8054)
* [@vincent-hachin-wmx](https://github.com/vincent-hachin-wmx) made their first contribution in [#8138](https://github.com/pydantic/pydantic/pull/8138)
* [@QuentinSoubeyranAqemia](https://github.com/QuentinSoubeyranAqemia) made their first contribution in [#7825](https://github.com/pydantic/pydantic/pull/7825)
* [@ariebovenberg](https://github.com/ariebovenberg) made their first contribution in [#8072](https://github.com/pydantic/pydantic/pull/8072)
* [@LukeTonin](https://github.com/LukeTonin) made their first contribution in [#8223](https://github.com/pydantic/pydantic/pull/8223)
* [@denisart](https://github.com/denisart) made their first contribution in [#8231](https://github.com/pydantic/pydantic/pull/8231)
* [@ianhfc](https://github.com/ianhfc) made their first contribution in [#8066](https://github.com/pydantic/pydantic/pull/8066)
* [@eonu](https://github.com/eonu) made their first contribution in [#8255](https://github.com/pydantic/pydantic/pull/8255)
* [@amandahla](https://github.com/amandahla) made their first contribution in [#8263](https://github.com/pydantic/pydantic/pull/8263)
* [@ibleedicare](https://github.com/ibleedicare) made their first contribution in [#8262](https://github.com/pydantic/pydantic/pull/8262)
* [@jevins09](https://github.com/jevins09) made their first contribution in [#8316](https://github.com/pydantic/pydantic/pull/8316)
* [@cuu508](https://github.com/cuu508) made their first contribution in [#8322](https://github.com/pydantic/pydantic/pull/8322)
* [@slanzmich](https://github.com/slanzmich) made their first contribution in [#8305](https://github.com/pydantic/pydantic/pull/8305)
* [@jensenbox](https://github.com/jensenbox) made their first contribution in [#8331](https://github.com/pydantic/pydantic/pull/8331)
* [@szepeviktor](https://github.com/szepeviktor) made their first contribution in [#8356](https://github.com/pydantic/pydantic/pull/8356)
* [@Elkiwa](https://github.com/Elkiwa) made their first contribution in [#8341](https://github.com/pydantic/pydantic/pull/8341)
* [@parhamfh](https://github.com/parhamfh) made their first contribution in [#8395](https://github.com/pydantic/pydantic/pull/8395)
* [@shenxiangzhuang](https://github.com/shenxiangzhuang) made their first contribution in [#8402](https://github.com/pydantic/pydantic/pull/8402)
* [@NeevCohen](https://github.com/NeevCohen) made their first contribution in [#8387](https://github.com/pydantic/pydantic/pull/8387)
* [@zby](https://github.com/zby) made their first contribution in [#8497](https://github.com/pydantic/pydantic/pull/8497)
* [@patelnets](https://github.com/patelnets) made their first contribution in [#8491](https://github.com/pydantic/pydantic/pull/8491)
* [@edwardwli](https://github.com/edwardwli) made their first contribution in [#8503](https://github.com/pydantic/pydantic/pull/8503)
* [@luca-matei](https://github.com/luca-matei) made their first contribution in [#8507](https://github.com/pydantic/pydantic/pull/8507)
* [@Jocelyn-Gas](https://github.com/Jocelyn-Gas) made their first contribution in [#8437](https://github.com/pydantic/pydantic/pull/8437)
* [@bL34cHig0](https://github.com/bL34cHig0) made their first contribution in [#8501](https://github.com/pydantic/pydantic/pull/8501)
* [@tigeryy2](https://github.com/tigeryy2) made their first contribution in [#8511](https://github.com/pydantic/pydantic/pull/8511)
* [@geospackle](https://github.com/geospackle) made their first contribution in [#8537](https://github.com/pydantic/pydantic/pull/8537)
* [@Anvil](https://github.com/Anvil) made their first contribution in [#8567](https://github.com/pydantic/pydantic/pull/8567)
* [@hungtsetse](https://github.com/hungtsetse) made their first contribution in [#8546](https://github.com/pydantic/pydantic/pull/8546)
* [@StrawHatDrag0n](https://github.com/StrawHatDrag0n) made their first contribution in [#8583](https://github.com/pydantic/pydantic/pull/8583)

#### `pydantic-core`

* [@mariuswinger](https://github.com/mariuswinger) made their first contribution in [pydantic/pydantic-core#1087](https://github.com/pydantic/pydantic-core/pull/1087)
* [@adamchainz](https://github.com/adamchainz) made their first contribution in [pydantic/pydantic-core#1090](https://github.com/pydantic/pydantic-core/pull/1090)
* [@akx](https://github.com/akx) made their first contribution in [pydantic/pydantic-core#1123](https://github.com/pydantic/pydantic-core/pull/1123)

## v2.6.0b1 (2024-01-19)

Pre-release, see [the GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.6.0b1) for details.

## V2.5.3 (2023-12-22)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.5.3)

### What's Changed

#### Packaging

* uprev `pydantic-core` to 2.14.6

#### Fixes

* Fix memory leak with recursive definitions creating reference cycles by [@davidhewitt](https://github.com/davidhewitt) in [pydantic/pydantic-core#1125](https://github.com/pydantic/pydantic-core/pull/1125)

## V2.5.2 (2023-11-22)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.5.2)

### What's Changed

#### Packaging

* uprev `pydantic-core` to 2.14.5

#### New Features

* Add `ConfigDict.ser_json_inf_nan` by [@davidhewitt](https://github.com/davidhewitt) in [#8159](https://github.com/pydantic/pydantic/pull/8159)

#### Fixes

* Fix validation of `Literal` from JSON keys when used as `dict` key by [@sydney-runkle](https://github.com/sydney-runkle) in [pydantic/pydantic-core#1075](https://github.com/pydantic/pydantic-core/pull/1075)
* Fix bug re `custom_init` on members of `Union` by [@sydney-runkle](https://github.com/sydney-runkle) in [pydantic/pydantic-core#1076](https://github.com/pydantic/pydantic-core/pull/1076)
* Fix `JsonValue` `bool` serialization by [@sydney-runkle](https://github.com/sydney-runkle) in [#8190](https://github.com/pydantic/pydantic/pull/8159)
* Fix handling of unhashable inputs with `Literal` in `Union`s by [@sydney-runkle](https://github.com/sydney-runkle) in [pydantic/pydantic-core#1089](https://github.com/pydantic/pydantic-core/pull/1089)

## V2.5.1 (2023-11-15)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.5.1)

### What's Changed

#### Packaging

* uprev pydantic-core to 2.14.3 by [@samuelcolvin](https://github.com/samuelcolvin) in [#8120](https://github.com/pydantic/pydantic/pull/8120)

#### Fixes

* Fix package description limit by [@dmontagu](https://github.com/dmontagu) in [#8097](https://github.com/pydantic/pydantic/pull/8097)
* Fix `ValidateCallWrapper` error when creating a model which has a [@validate_call](https://github.com/validate_call) wrapped field annotation by [@sydney-runkle](https://github.com/sydney-runkle) in [#8110](https://github.com/pydantic/pydantic/pull/8110)

## V2.5.0 (2023-11-13)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.5.0)

The code released in v2.5.0 is functionally identical to that of v2.5.0b1.

### What's Changed

#### Packaging

* Update pydantic-core from 2.10.1 to 2.14.1, significant changes from these updates are described below, full changelog [here](https://github.com/pydantic/pydantic-core/compare/v2.10.1...v2.14.1)
* Update to `pyright==1.1.335` by [@Viicos](https://github.com/Viicos) in [#8075](https://github.com/pydantic/pydantic/pull/8075)

#### New Features

* Allow plugins to catch non `ValidationError` errors by [@adriangb](https://github.com/adriangb) in [#7806](https://github.com/pydantic/pydantic/pull/7806)
* Support `__doc__` argument in `create_model()` by [@chris-spann](https://github.com/chris-spann) in [#7863](https://github.com/pydantic/pydantic/pull/7863)
* Expose `regex_engine` flag - meaning you can use with the Rust or Python regex libraries in constraints by [@utkini](https://github.com/utkini) in [#7768](https://github.com/pydantic/pydantic/pull/7768)
* Save return type generated from type annotation in `ComputedFieldInfo` by [@alexmojaki](https://github.com/alexmojaki) in [#7889](https://github.com/pydantic/pydantic/pull/7889)
* Adopting `ruff` formatter by [@Luca-Blight](https://github.com/Luca-Blight) in [#7930](https://github.com/pydantic/pydantic/pull/7930)
* Added `validation_error_cause` to config by [@zakstucke](https://github.com/zakstucke) in [#7626](https://github.com/pydantic/pydantic/pull/7626)
* Make path of the item to validate available in plugin by [@hramezani](https://github.com/hramezani) in [#7861](https://github.com/pydantic/pydantic/pull/7861)
* Add `CallableDiscriminator` and `Tag` by [@dmontagu](https://github.com/dmontagu) in [#7983](https://github.com/pydantic/pydantic/pull/7983)
  * `CallableDiscriminator` renamed to `Discriminator` by [@dmontagu](https://github.com/dmontagu) in [#8047](https://github.com/pydantic/pydantic/pull/8047)
* Make union case tags affect union error messages by [@dmontagu](https://github.com/dmontagu) in [#8001](https://github.com/pydantic/pydantic/pull/8001)
* Add `examples` and `json_schema_extra` to `@computed_field` by [@alexmojaki](https://github.com/alexmojaki) in [#8013](https://github.com/pydantic/pydantic/pull/8013)
* Add `JsonValue` type by [@dmontagu](https://github.com/dmontagu) in [#7998](https://github.com/pydantic/pydantic/pull/7998)
* Allow `str` as argument to `Discriminator` by [@dmontagu](https://github.com/dmontagu) in [#8047](https://github.com/pydantic/pydantic/pull/8047)
* Add `SchemaSerializer.__reduce__` method to enable pickle serialization by [@edoakes](https://github.com/edoakes) in [pydantic/pydantic-core#1006](https://github.com/pydantic/pydantic-core/pull/1006)

#### Changes

* **Significant Change:** replace `ultra_strict` with new smart union implementation, the way unions are validated has changed significantly to improve performance and correctness, we have worked hard to absolutely minimise the number of cases where behaviour has changed, see the PR for details - by [@davidhewitt](https://github.com/davidhewitt) in [pydantic/pydantic-core#867](https://github.com/pydantic/pydantic-core/pull/867)
* Add support for instance method reassignment when `extra='allow'` by [@sydney-runkle](https://github.com/sydney-runkle) in [#7683](https://github.com/pydantic/pydantic/pull/7683)
* Support JSON schema generation for `Enum` types with no cases by [@sydney-runkle](https://github.com/sydney-runkle) in [#7927](https://github.com/pydantic/pydantic/pull/7927)
* Warn if a class inherits from `Generic` before `BaseModel` by [@alexmojaki](https://github.com/alexmojaki) in [#7891](https://github.com/pydantic/pydantic/pull/7891)

#### Performance

* New custom JSON parser, `jiter` by [@samuelcolvin](https://github.com/samuelcolvin) in [pydantic/pydantic-core#974](https://github.com/pydantic/pydantic-core/pull/974)
* PGO build for MacOS M1 by [@samuelcolvin](https://github.com/samuelcolvin) in [pydantic/pydantic-core#1063](https://github.com/pydantic/pydantic-core/pull/1063)
* Use `__getattr__` for all package imports, improve import time by [@samuelcolvin](https://github.com/samuelcolvin) in [#7947](https://github.com/pydantic/pydantic/pull/7947)

#### Fixes

* Fix `mypy` issue with subclasses of `RootModel` by [@sydney-runkle](https://github.com/sydney-runkle) in [#7677](https://github.com/pydantic/pydantic/pull/7677)
* Properly rebuild the `FieldInfo` when a forward ref gets evaluated by [@dmontagu](https://github.com/dmontagu) in [#7698](https://github.com/pydantic/pydantic/pull/7698)
* Fix failure to load `SecretStr` from JSON (regression in v2.4) by [@sydney-runkle](https://github.com/sydney-runkle) in [#7729](https://github.com/pydantic/pydantic/pull/7729)
* Fix `defer_build` behavior with `TypeAdapter` by [@sydney-runkle](https://github.com/sydney-runkle) in [#7736](https://github.com/pydantic/pydantic/pull/7736)
* Improve compatibility with legacy `mypy` versions by [@dmontagu](https://github.com/dmontagu) in [#7742](https://github.com/pydantic/pydantic/pull/7742)
* Fix: update `TypeVar` handling when default is not set by [@pmmmwh](https://github.com/pmmmwh) in [#7719](https://github.com/pydantic/pydantic/pull/7719)
* Support specification of `strict` on `Enum` type fields by [@sydney-runkle](https://github.com/sydney-runkle) in [#7761](https://github.com/pydantic/pydantic/pull/7761)
* Wrap `weakref.ref` instead of subclassing to fix `cloudpickle` serialization by [@edoakes](https://github.com/edoakes) in [#7780](https://github.com/pydantic/pydantic/pull/7780)
* Keep values of private attributes set within `model_post_init` in subclasses by [@alexmojaki](https://github.com/alexmojaki) in [#7775](https://github.com/pydantic/pydantic/pull/7775)
* Add more specific type for non-callable `json_schema_extra` by [@alexmojaki](https://github.com/alexmojaki) in [#7803](https://github.com/pydantic/pydantic/pull/7803)
* Raise an error when deleting frozen (model) fields by [@alexmojaki](https://github.com/alexmojaki) in [#7800](https://github.com/pydantic/pydantic/pull/7800)
* Fix schema sorting bug with default values by [@sydney-runkle](https://github.com/sydney-runkle) in [#7817](https://github.com/pydantic/pydantic/pull/7817)
* Use generated alias for aliases that are not specified otherwise by [@alexmojaki](https://github.com/alexmojaki) in [#7802](https://github.com/pydantic/pydantic/pull/7802)
* Support `strict` specification for `UUID` types by [@sydney-runkle](https://github.com/sydney-runkle) in [#7865](https://github.com/pydantic/pydantic/pull/7865)
* JSON schema: fix extra parameter handling by [@me-and](https://github.com/me-and) in [#7810](https://github.com/pydantic/pydantic/pull/7810)
* Fix: support `pydantic.Field(kw_only=True)` with inherited dataclasses by [@PrettyWood](https://github.com/PrettyWood) in [#7827](https://github.com/pydantic/pydantic/pull/7827)
* Support `validate_call` decorator for methods in classes with `__slots__` by [@sydney-runkle](https://github.com/sydney-runkle) in [#7883](https://github.com/pydantic/pydantic/pull/7883)
* Fix pydantic dataclass problem with `dataclasses.field` default by [@hramezani](https://github.com/hramezani) in [#7898](https://github.com/pydantic/pydantic/pull/7898)
* Fix schema generation for generics with union type bounds by [@sydney-runkle](https://github.com/sydney-runkle) in [#7899](https://github.com/pydantic/pydantic/pull/7899)
* Fix version for `importlib_metadata` on python 3.7 by [@sydney-runkle](https://github.com/sydney-runkle) in [#7904](https://github.com/pydantic/pydantic/pull/7904)
* Support `|` operator (Union) in PydanticRecursiveRef by [@alexmojaki](https://github.com/alexmojaki) in [#7892](https://github.com/pydantic/pydantic/pull/7892)
* Fix `display_as_type` for `TypeAliasType` in python 3.12 by [@dmontagu](https://github.com/dmontagu) in [#7929](https://github.com/pydantic/pydantic/pull/7929)
* Add support for `NotRequired` generics in `TypedDict` by [@sydney-runkle](https://github.com/sydney-runkle) in [#7932](https://github.com/pydantic/pydantic/pull/7932)
* Make generic `TypeAliasType` specifications produce different schema definitions by [@alexdrydew](https://github.com/alexdrydew) in [#7893](https://github.com/pydantic/pydantic/pull/7893)
* Added fix for signature of inherited dataclass by [@howsunjow](https://github.com/howsunjow) in [#7925](https://github.com/pydantic/pydantic/pull/7925)
* Make the model name generation more robust in JSON schema by [@joakimnordling](https://github.com/joakimnordling) in [#7881](https://github.com/pydantic/pydantic/pull/7881)
* Fix plurals in validation error messages (in tests) by [@Iipin](https://github.com/Iipin) in [#7972](https://github.com/pydantic/pydantic/pull/7972)
* `PrivateAttr` is passed from `Annotated` default position by [@tabassco](https://github.com/tabassco) in [#8004](https://github.com/pydantic/pydantic/pull/8004)
* Don't decode bytes (which may not be UTF8) when displaying SecretBytes by [@alexmojaki](https://github.com/alexmojaki) in [#8012](https://github.com/pydantic/pydantic/pull/8012)
* Use `classmethod` instead of `classmethod[Any, Any, Any]` by [@Mr-Pepe](https://github.com/Mr-Pepe) in [#7979](https://github.com/pydantic/pydantic/pull/7979)
* Clearer error on invalid Plugin by [@samuelcolvin](https://github.com/samuelcolvin) in [#8023](https://github.com/pydantic/pydantic/pull/8023)
* Correct pydantic dataclasses import by [@samuelcolvin](https://github.com/samuelcolvin) in [#8027](https://github.com/pydantic/pydantic/pull/8027)
* Fix misbehavior for models referencing redefined type aliases by [@dmontagu](https://github.com/dmontagu) in [#8050](https://github.com/pydantic/pydantic/pull/8050)
* Fix `Optional` field with `validate_default` only performing one field validation by [@sydney-runkle](https://github.com/sydney-runkle) in [pydantic/pydantic-core#1002](https://github.com/pydantic/pydantic-core/pull/1002)
* Fix `definition-ref` bug with `Dict` keys by [@sydney-runkle](https://github.com/sydney-runkle) in [pydantic/pydantic-core#1014](https://github.com/pydantic/pydantic-core/pull/1014)
* Fix bug allowing validation of `bool` types with `coerce_numbers_to_str=True` by [@sydney-runkle](https://github.com/sydney-runkle) in [pydantic/pydantic-core#1017](https://github.com/pydantic/pydantic-core/pull/1017)
* Don't accept `NaN` in float and decimal constraints by [@davidhewitt](https://github.com/davidhewitt) in [pydantic/pydantic-core#1037](https://github.com/pydantic/pydantic-core/pull/1037)
* Add `lax_str` and `lax_int` support for enum values not inherited from str/int by [@michaelhly](https://github.com/michaelhly) in [pydantic/pydantic-core#1015](https://github.com/pydantic/pydantic-core/pull/1015)
* Support subclasses in lists in `Union` of `List` types by [@sydney-runkle](https://github.com/sydney-runkle) in [pydantic/pydantic-core#1039](https://github.com/pydantic/pydantic-core/pull/1039)
* Allow validation against `max_digits` and `decimals` to pass if normalized or non-normalized input is valid by [@sydney-runkle](https://github.com/sydney-runkle) in [pydantic/pydantic-core#1049](https://github.com/pydantic/pydantic-core/pull/1049)
* Fix: proper pluralization in `ValidationError` messages by [@Iipin](https://github.com/Iipin) in [pydantic/pydantic-core#1050](https://github.com/pydantic/pydantic-core/pull/1050)
* Disallow the string `'-'` as `datetime` input by [@davidhewitt](https://github.com/davidhewitt) in [pydantic/speedate#52](https://github.com/pydantic/speedate/pull/52) & [pydantic/pydantic-core#1060](https://github.com/pydantic/pydantic-core/pull/1060)
* Fix: NaN and Inf float serialization by [@davidhewitt](https://github.com/davidhewitt) in [pydantic/pydantic-core#1062](https://github.com/pydantic/pydantic-core/pull/1062)
* Restore manylinux-compatible PGO builds by [@davidhewitt](https://github.com/davidhewitt) in [pydantic/pydantic-core#1068](https://github.com/pydantic/pydantic-core/pull/1068)

### New Contributors

#### `pydantic`

* [@schneebuzz](https://github.com/schneebuzz) made their first contribution in [#7699](https://github.com/pydantic/pydantic/pull/7699)
* [@edoakes](https://github.com/edoakes) made their first contribution in [#7780](https://github.com/pydantic/pydantic/pull/7780)
* [@alexmojaki](https://github.com/alexmojaki) made their first contribution in [#7775](https://github.com/pydantic/pydantic/pull/7775)
* [@NickG123](https://github.com/NickG123) made their first contribution in [#7751](https://github.com/pydantic/pydantic/pull/7751)
* [@gowthamgts](https://github.com/gowthamgts) made their first contribution in [#7830](https://github.com/pydantic/pydantic/pull/7830)
* [@jamesbraza](https://github.com/jamesbraza) made their first contribution in [#7848](https://github.com/pydantic/pydantic/pull/7848)
* [@laundmo](https://github.com/laundmo) made their first contribution in [#7850](https://github.com/pydantic/pydantic/pull/7850)
* [@rahmatnazali](https://github.com/rahmatnazali) made their first contribution in [#7870](https://github.com/pydantic/pydantic/pull/7870)
* [@waterfountain1996](https://github.com/waterfountain1996) made their first contribution in [#7878](https://github.com/pydantic/pydantic/pull/7878)
* [@chris-spann](https://github.com/chris-spann) made their first contribution in [#7863](https://github.com/pydantic/pydantic/pull/7863)
* [@me-and](https://github.com/me-and) made their first contribution in [#7810](https://github.com/pydantic/pydantic/pull/7810)
* [@utkini](https://github.com/utkini) made their first contribution in [#7768](https://github.com/pydantic/pydantic/pull/7768)
* [@bn-l](https://github.com/bn-l) made their first contribution in [#7744](https://github.com/pydantic/pydantic/pull/7744)
* [@alexdrydew](https://github.com/alexdrydew) made their first contribution in [#7893](https://github.com/pydantic/pydantic/pull/7893)
* [@Luca-Blight](https://github.com/Luca-Blight) made their first contribution in [#7930](https://github.com/pydantic/pydantic/pull/7930)
* [@howsunjow](https://github.com/howsunjow) made their first contribution in [#7925](https://github.com/pydantic/pydantic/pull/7925)
* [@joakimnordling](https://github.com/joakimnordling) made their first contribution in [#7881](https://github.com/pydantic/pydantic/pull/7881)
* [@icfly2](https://github.com/icfly2) made their first contribution in [#7976](https://github.com/pydantic/pydantic/pull/7976)
* [@Yummy-Yums](https://github.com/Yummy-Yums) made their first contribution in [#8003](https://github.com/pydantic/pydantic/pull/8003)
* [@Iipin](https://github.com/Iipin) made their first contribution in [#7972](https://github.com/pydantic/pydantic/pull/7972)
* [@tabassco](https://github.com/tabassco) made their first contribution in [#8004](https://github.com/pydantic/pydantic/pull/8004)
* [@Mr-Pepe](https://github.com/Mr-Pepe) made their first contribution in [#7979](https://github.com/pydantic/pydantic/pull/7979)
* [@0x00cl](https://github.com/0x00cl) made their first contribution in [#8010](https://github.com/pydantic/pydantic/pull/8010)
* [@barraponto](https://github.com/barraponto) made their first contribution in [#8032](https://github.com/pydantic/pydantic/pull/8032)

#### `pydantic-core`

* [@sisp](https://github.com/sisp) made their first contribution in [pydantic/pydantic-core#995](https://github.com/pydantic/pydantic-core/pull/995)
* [@michaelhly](https://github.com/michaelhly) made their first contribution in [pydantic/pydantic-core#1015](https://github.com/pydantic/pydantic-core/pull/1015)

## v2.5.0b1 (2023-11-09)

Pre-release, see [the GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.5.0b1) for details.

## V2.4.2 (2023-09-27)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.4.2)

### What's Changed

#### Fixes

* Fix bug with JSON schema for sequence of discriminated union by [@dmontagu](https://github.com/dmontagu) in [#7647](https://github.com/pydantic/pydantic/pull/7647)
* Fix schema references in discriminated unions by [@adriangb](https://github.com/adriangb) in [#7646](https://github.com/pydantic/pydantic/pull/7646)
* Fix json schema generation for recursive models by [@adriangb](https://github.com/adriangb) in [#7653](https://github.com/pydantic/pydantic/pull/7653)
* Fix `models_json_schema` for generic models by [@adriangb](https://github.com/adriangb) in [#7654](https://github.com/pydantic/pydantic/pull/7654)
* Fix xfailed test for generic model signatures by [@adriangb](https://github.com/adriangb) in [#7658](https://github.com/pydantic/pydantic/pull/7658)

### New Contributors

* [@austinorr](https://github.com/austinorr) made their first contribution in [#7657](https://github.com/pydantic/pydantic/pull/7657)
* [@peterHoburg](https://github.com/peterHoburg) made their first contribution in [#7670](https://github.com/pydantic/pydantic/pull/7670)

## V2.4.1 (2023-09-26)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.4.1)

### What's Changed

#### Packaging

* Update pydantic-core to 2.10.1 by [@davidhewitt](https://github.com/davidhewitt) in [#7633](https://github.com/pydantic/pydantic/pull/7633)

#### Fixes

* Serialize unsubstituted type vars as `Any` by [@adriangb](https://github.com/adriangb) in [#7606](https://github.com/pydantic/pydantic/pull/7606)
* Remove schema building caches by [@adriangb](https://github.com/adriangb) in [#7624](https://github.com/pydantic/pydantic/pull/7624)
* Fix an issue where JSON schema extras weren't JSON encoded by [@dmontagu](https://github.com/dmontagu) in [#7625](https://github.com/pydantic/pydantic/pull/7625)

## V2.4.0 (2023-09-22)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.4.0)

### What's Changed

#### Packaging

* Update pydantic-core to 2.10.0 by [@samuelcolvin](https://github.com/samuelcolvin) in [#7542](https://github.com/pydantic/pydantic/pull/7542)

#### New Features

* Add `Base64Url` types by [@dmontagu](https://github.com/dmontagu) in [#7286](https://github.com/pydantic/pydantic/pull/7286)
* Implement optional `number` to `str` coercion by [@lig](https://github.com/lig) in [#7508](https://github.com/pydantic/pydantic/pull/7508)
* Allow access to `field_name` and `data` in all validators if there is data and a field name by [@samuelcolvin](https://github.com/samuelcolvin) in [#7542](https://github.com/pydantic/pydantic/pull/7542)
* Add `BaseModel.model_validate_strings` and `TypeAdapter.validate_strings` by [@hramezani](https://github.com/hramezani) in [#7552](https://github.com/pydantic/pydantic/pull/7552)
* Add Pydantic `plugins` experimental implementation by [@lig](https://github.com/lig) [@samuelcolvin](https://github.com/samuelcolvin) and [@Kludex](https://github.com/Kludex) in [#6820](https://github.com/pydantic/pydantic/pull/6820)

#### Changes

* Do not override `model_post_init` in subclass with private attrs by [@Viicos](https://github.com/Viicos) in [#7302](https://github.com/pydantic/pydantic/pull/7302)
* Make fields with defaults not required in the serialization schema by default by [@dmontagu](https://github.com/dmontagu) in [#7275](https://github.com/pydantic/pydantic/pull/7275)
* Mark `Extra` as deprecated by [@disrupted](https://github.com/disrupted) in [#7299](https://github.com/pydantic/pydantic/pull/7299)
* Make `EncodedStr` a dataclass by [@Kludex](https://github.com/Kludex) in [#7396](https://github.com/pydantic/pydantic/pull/7396)
* Move `annotated_handlers` to be public by [@samuelcolvin](https://github.com/samuelcolvin) in [#7569](https://github.com/pydantic/pydantic/pull/7569)

#### Performance

* Simplify flattening and inlining of `CoreSchema` by [@adriangb](https://github.com/adriangb) in [#7523](https://github.com/pydantic/pydantic/pull/7523)
* Remove unused copies in `CoreSchema` walking by [@adriangb](https://github.com/adriangb) in [#7528](https://github.com/pydantic/pydantic/pull/7528)
* Add caches for collecting definitions and invalid schemas from a CoreSchema by [@adriangb](https://github.com/adriangb) in [#7527](https://github.com/pydantic/pydantic/pull/7527)
* Eagerly resolve discriminated unions and cache cases where we can't by [@adriangb](https://github.com/adriangb) in [#7529](https://github.com/pydantic/pydantic/pull/7529)
* Replace `dict.get` and `dict.setdefault` with more verbose versions in `CoreSchema` building hot paths by [@adriangb](https://github.com/adriangb) in [#7536](https://github.com/pydantic/pydantic/pull/7536)
* Cache invalid `CoreSchema` discovery by [@adriangb](https://github.com/adriangb) in [#7535](https://github.com/pydantic/pydantic/pull/7535)
* Allow disabling `CoreSchema` validation for faster startup times by [@adriangb](https://github.com/adriangb) in [#7565](https://github.com/pydantic/pydantic/pull/7565)

#### Fixes

* Fix config detection for `TypedDict` from grandparent classes by [@dmontagu](https://github.com/dmontagu) in [#7272](https://github.com/pydantic/pydantic/pull/7272)
* Fix hash function generation for frozen models with unusual MRO by [@dmontagu](https://github.com/dmontagu) in [#7274](https://github.com/pydantic/pydantic/pull/7274)
* Make `strict` config overridable in field for Path by [@hramezani](https://github.com/hramezani) in [#7281](https://github.com/pydantic/pydantic/pull/7281)
* Use `ser_json_<timedelta|bytes>` on default in `GenerateJsonSchema` by [@Kludex](https://github.com/Kludex) in [#7269](https://github.com/pydantic/pydantic/pull/7269)
* Adding a check that alias is validated as an identifier for Python by [@andree0](https://github.com/andree0) in [#7319](https://github.com/pydantic/pydantic/pull/7319)
* Raise an error when computed field overrides field by [@sydney-runkle](https://github.com/sydney-runkle) in [#7346](https://github.com/pydantic/pydantic/pull/7346)
* Fix applying `SkipValidation` to referenced schemas by [@adriangb](https://github.com/adriangb) in [#7381](https://github.com/pydantic/pydantic/pull/7381)
* Enforce behavior of private attributes having double leading underscore by [@lig](https://github.com/lig) in [#7265](https://github.com/pydantic/pydantic/pull/7265)
* Standardize `__get_pydantic_core_schema__` signature by [@hramezani](https://github.com/hramezani) in [#7415](https://github.com/pydantic/pydantic/pull/7415)
* Fix generic dataclass fields mutation bug (when using `TypeAdapter`) by [@sydney-runkle](https://github.com/sydney-runkle) in [#7435](https://github.com/pydantic/pydantic/pull/7435)
* Fix `TypeError` on `model_validator` in `wrap` mode by [@pmmmwh](https://github.com/pmmmwh) in [#7496](https://github.com/pydantic/pydantic/pull/7496)
* Improve enum error message by [@hramezani](https://github.com/hramezani) in [#7506](https://github.com/pydantic/pydantic/pull/7506)
* Make `repr` work for instances that failed initialization when handling `ValidationError`s by [@dmontagu](https://github.com/dmontagu) in [#7439](https://github.com/pydantic/pydantic/pull/7439)
* Fixed a regular expression denial of service issue by limiting whitespaces by [@prodigysml](https://github.com/prodigysml) in [#7360](https://github.com/pydantic/pydantic/pull/7360)
* Fix handling of `UUID` values having `UUID.version=None` by [@lig](https://github.com/lig) in [#7566](https://github.com/pydantic/pydantic/pull/7566)
* Fix `__iter__` returning private `cached_property` info by [@sydney-runkle](https://github.com/sydney-runkle) in [#7570](https://github.com/pydantic/pydantic/pull/7570)
* Improvements to version info message by [@samuelcolvin](https://github.com/samuelcolvin) in [#7594](https://github.com/pydantic/pydantic/pull/7594)

### New Contributors

* [@15498th](https://github.com/15498th) made their first contribution in [#7238](https://github.com/pydantic/pydantic/pull/7238)
* [@GabrielCappelli](https://github.com/GabrielCappelli) made their first contribution in [#7213](https://github.com/pydantic/pydantic/pull/7213)
* [@tobni](https://github.com/tobni) made their first contribution in [#7184](https://github.com/pydantic/pydantic/pull/7184)
* [@redruin1](https://github.com/redruin1) made their first contribution in [#7282](https://github.com/pydantic/pydantic/pull/7282)
* [@FacerAin](https://github.com/FacerAin) made their first contribution in [#7288](https://github.com/pydantic/pydantic/pull/7288)
* [@acdha](https://github.com/acdha) made their first contribution in [#7297](https://github.com/pydantic/pydantic/pull/7297)
* [@andree0](https://github.com/andree0) made their first contribution in [#7319](https://github.com/pydantic/pydantic/pull/7319)
* [@gordonhart](https://github.com/gordonhart) made their first contribution in [#7375](https://github.com/pydantic/pydantic/pull/7375)
* [@pmmmwh](https://github.com/pmmmwh) made their first contribution in [#7496](https://github.com/pydantic/pydantic/pull/7496)
* [@disrupted](https://github.com/disrupted) made their first contribution in [#7299](https://github.com/pydantic/pydantic/pull/7299)
* [@prodigysml](https://github.com/prodigysml) made their first contribution in [#7360](https://github.com/pydantic/pydantic/pull/7360)

## V2.3.0 (2023-08-23)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.3.0)

* 🔥 Remove orphaned changes file from repo by [@lig](https://github.com/lig) in [#7168](https://github.com/pydantic/pydantic/pull/7168)
* Add copy button on documentation by [@Kludex](https://github.com/Kludex) in [#7190](https://github.com/pydantic/pydantic/pull/7190)
* Fix docs on JSON type by [@Kludex](https://github.com/Kludex) in [#7189](https://github.com/pydantic/pydantic/pull/7189)
* Update mypy 1.5.0 to 1.5.1 in CI by [@hramezani](https://github.com/hramezani) in [#7191](https://github.com/pydantic/pydantic/pull/7191)
* fix download links badge by [@samuelcolvin](https://github.com/samuelcolvin) in [#7200](https://github.com/pydantic/pydantic/pull/7200)
* add 2.2.1 to changelog by [@samuelcolvin](https://github.com/samuelcolvin) in [#7212](https://github.com/pydantic/pydantic/pull/7212)
* Make ModelWrapValidator protocols generic by [@dmontagu](https://github.com/dmontagu) in [#7154](https://github.com/pydantic/pydantic/pull/7154)
* Correct `Field(..., exclude: bool)` docs by [@samuelcolvin](https://github.com/samuelcolvin) in [#7214](https://github.com/pydantic/pydantic/pull/7214)
* Make shadowing attributes a warning instead of an error by [@adriangb](https://github.com/adriangb) in [#7193](https://github.com/pydantic/pydantic/pull/7193)
* Document `Base64Str` and `Base64Bytes` by [@Kludex](https://github.com/Kludex) in [#7192](https://github.com/pydantic/pydantic/pull/7192)
* Fix `config.defer_build` for serialization first cases by [@samuelcolvin](https://github.com/samuelcolvin) in [#7024](https://github.com/pydantic/pydantic/pull/7024)
* clean Model docstrings in JSON Schema by [@samuelcolvin](https://github.com/samuelcolvin) in [#7210](https://github.com/pydantic/pydantic/pull/7210)
* fix [#7228](https://github.com/pydantic/pydantic/pull/7228) (typo): docs in `validators.md` to correct `validate_default` kwarg by [@lmmx](https://github.com/lmmx) in [#7229](https://github.com/pydantic/pydantic/pull/7229)
* ✅ Implement `tzinfo.fromutc` method for `TzInfo` in `pydantic-core` by [@lig](https://github.com/lig) in [#7019](https://github.com/pydantic/pydantic/pull/7019)
* Support `__get_validators__` by [@hramezani](https://github.com/hramezani) in [#7197](https://github.com/pydantic/pydantic/pull/7197)

## V2.2.1 (2023-08-18)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.2.1)

* Make `xfail`ing test for root model extra stop `xfail`ing by [@dmontagu](https://github.com/dmontagu) in [#6937](https://github.com/pydantic/pydantic/pull/6937)
* Optimize recursion detection by stopping on the second visit for the same object by [@mciucu](https://github.com/mciucu) in [#7160](https://github.com/pydantic/pydantic/pull/7160)
* fix link in docs by [@tlambert03](https://github.com/tlambert03) in [#7166](https://github.com/pydantic/pydantic/pull/7166)
* Replace MiMalloc w/ default allocator by [@adriangb](https://github.com/adriangb) in [pydantic/pydantic-core#900](https://github.com/pydantic/pydantic-core/pull/900)
* Bump pydantic-core to 2.6.1 and prepare 2.2.1 release by [@adriangb](https://github.com/adriangb) in [#7176](https://github.com/pydantic/pydantic/pull/7176)

## V2.2.0 (2023-08-17)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.2.0)

* Split "pipx install" setup command into two commands on the documentation site by [@nomadmtb](https://github.com/nomadmtb) in [#6869](https://github.com/pydantic/pydantic/pull/6869)
* Deprecate `Field.include` by [@hramezani](https://github.com/hramezani) in [#6852](https://github.com/pydantic/pydantic/pull/6852)
* Fix typo in default factory error msg by [@hramezani](https://github.com/hramezani) in [#6880](https://github.com/pydantic/pydantic/pull/6880)
* Simplify handling of typing.Annotated in GenerateSchema by [@dmontagu](https://github.com/dmontagu) in [#6887](https://github.com/pydantic/pydantic/pull/6887)
* Re-enable fastapi tests in CI by [@dmontagu](https://github.com/dmontagu) in [#6883](https://github.com/pydantic/pydantic/pull/6883)
* Make it harder to hit collisions with json schema defrefs by [@dmontagu](https://github.com/dmontagu) in [#6566](https://github.com/pydantic/pydantic/pull/6566)
* Cleaner error for invalid input to `Path` fields by [@samuelcolvin](https://github.com/samuelcolvin) in [#6903](https://github.com/pydantic/pydantic/pull/6903)
* :memo: support Coordinate Type by [@yezz123](https://github.com/yezz123) in [#6906](https://github.com/pydantic/pydantic/pull/6906)
* Fix `ForwardRef` wrapper for py 3.10.0 (shim until bpo-45166) by [@randomir](https://github.com/randomir) in [#6919](https://github.com/pydantic/pydantic/pull/6919)
* Fix misbehavior related to copying of RootModel by [@dmontagu](https://github.com/dmontagu) in [#6918](https://github.com/pydantic/pydantic/pull/6918)
* Fix issue with recursion error caused by ParamSpec by [@dmontagu](https://github.com/dmontagu) in [#6923](https://github.com/pydantic/pydantic/pull/6923)
* Add section about Constrained classes to the Migration Guide by [@Kludex](https://github.com/Kludex) in [#6924](https://github.com/pydantic/pydantic/pull/6924)
* Use `main` branch for badge links by [@Viicos](https://github.com/Viicos) in [#6925](https://github.com/pydantic/pydantic/pull/6925)
* Add test for v1/v2 Annotated discrepancy by [@carlbordum](https://github.com/carlbordum) in [#6926](https://github.com/pydantic/pydantic/pull/6926)
* Make the v1 mypy plugin work with both v1 and v2 by [@dmontagu](https://github.com/dmontagu) in [#6921](https://github.com/pydantic/pydantic/pull/6921)
* Fix issue where generic models couldn't be parametrized with BaseModel by [@dmontagu](https://github.com/dmontagu) in [#6933](https://github.com/pydantic/pydantic/pull/6933)
* Remove xfail for discriminated union with alias by [@dmontagu](https://github.com/dmontagu) in [#6938](https://github.com/pydantic/pydantic/pull/6938)
* add field_serializer to computed_field by [@andresliszt](https://github.com/andresliszt) in [#6965](https://github.com/pydantic/pydantic/pull/6965)
* Use union_schema with Type[Union[...]] by [@JeanArhancet](https://github.com/JeanArhancet) in [#6952](https://github.com/pydantic/pydantic/pull/6952)
* Fix inherited typeddict attributes / config by [@adriangb](https://github.com/adriangb) in [#6981](https://github.com/pydantic/pydantic/pull/6981)
* fix dataclass annotated before validator called twice by [@davidhewitt](https://github.com/davidhewitt) in [#6998](https://github.com/pydantic/pydantic/pull/6998)
* Update test-fastapi deselected tests by [@hramezani](https://github.com/hramezani) in [#7014](https://github.com/pydantic/pydantic/pull/7014)
* Fix validator doc format by [@hramezani](https://github.com/hramezani) in [#7015](https://github.com/pydantic/pydantic/pull/7015)
* Fix typo in docstring of model_json_schema by [@AdamVinch-Federated](https://github.com/AdamVinch-Federated) in [#7032](https://github.com/pydantic/pydantic/pull/7032)
* remove unused "type ignores" with pyright by [@samuelcolvin](https://github.com/samuelcolvin) in [#7026](https://github.com/pydantic/pydantic/pull/7026)
* Add benchmark representing FastAPI startup time by [@adriangb](https://github.com/adriangb) in [#7030](https://github.com/pydantic/pydantic/pull/7030)
* Fix json_encoders for Enum subclasses by [@adriangb](https://github.com/adriangb) in [#7029](https://github.com/pydantic/pydantic/pull/7029)
* Update docstring of `ser_json_bytes` regarding base64 encoding by [@Viicos](https://github.com/Viicos) in [#7052](https://github.com/pydantic/pydantic/pull/7052)
* Allow `@validate_call` to work on async methods by [@adriangb](https://github.com/adriangb) in [#7046](https://github.com/pydantic/pydantic/pull/7046)
* Fix: mypy error with `Settings` and `SettingsConfigDict` by [@JeanArhancet](https://github.com/JeanArhancet) in [#7002](https://github.com/pydantic/pydantic/pull/7002)
* Fix some typos (repeated words and it's/its) by [@eumiro](https://github.com/eumiro) in [#7063](https://github.com/pydantic/pydantic/pull/7063)
* Fix the typo in docstring by [@harunyasar](https://github.com/harunyasar) in [#7062](https://github.com/pydantic/pydantic/pull/7062)
* Docs: Fix broken URL in the pydantic-settings package recommendation by [@swetjen](https://github.com/swetjen) in [#6995](https://github.com/pydantic/pydantic/pull/6995)
* Handle constraints being applied to schemas that don't accept it by [@adriangb](https://github.com/adriangb) in [#6951](https://github.com/pydantic/pydantic/pull/6951)
* Replace almost_equal_floats with math.isclose by [@eumiro](https://github.com/eumiro) in [#7082](https://github.com/pydantic/pydantic/pull/7082)
* bump pydantic-core to 2.5.0 by [@davidhewitt](https://github.com/davidhewitt) in [#7077](https://github.com/pydantic/pydantic/pull/7077)
* Add `short_version` and use it in links by [@hramezani](https://github.com/hramezani) in [#7115](https://github.com/pydantic/pydantic/pull/7115)
* 📝 Add usage link to `RootModel` by [@Kludex](https://github.com/Kludex) in [#7113](https://github.com/pydantic/pydantic/pull/7113)
* Revert "Fix default port for mongosrv DSNs (#6827)" by [@Kludex](https://github.com/Kludex) in [#7116](https://github.com/pydantic/pydantic/pull/7116)
* Clarify validate_default and _Unset handling in usage docs and migration guide by [@benbenbang](https://github.com/benbenbang) in [#6950](https://github.com/pydantic/pydantic/pull/6950)
* Tweak documentation of `Field.exclude` by [@Viicos](https://github.com/Viicos) in [#7086](https://github.com/pydantic/pydantic/pull/7086)
* Do not require `validate_assignment` to use `Field.frozen` by [@Viicos](https://github.com/Viicos) in [#7103](https://github.com/pydantic/pydantic/pull/7103)
* tweaks to `_core_utils` by [@samuelcolvin](https://github.com/samuelcolvin) in [#7040](https://github.com/pydantic/pydantic/pull/7040)
* Make DefaultDict working with set by [@hramezani](https://github.com/hramezani) in [#7126](https://github.com/pydantic/pydantic/pull/7126)
* Don't always require typing.Generic as a base for partially parametrized models by [@dmontagu](https://github.com/dmontagu) in [#7119](https://github.com/pydantic/pydantic/pull/7119)
* Fix issue with JSON schema incorrectly using parent class core schema by [@dmontagu](https://github.com/dmontagu) in [#7020](https://github.com/pydantic/pydantic/pull/7020)
* Fix xfailed test related to TypedDict and alias_generator by [@dmontagu](https://github.com/dmontagu) in [#6940](https://github.com/pydantic/pydantic/pull/6940)
* Improve error message for NameEmail by [@dmontagu](https://github.com/dmontagu) in [#6939](https://github.com/pydantic/pydantic/pull/6939)
* Fix generic computed fields by [@dmontagu](https://github.com/dmontagu) in [#6988](https://github.com/pydantic/pydantic/pull/6988)
* Reflect namedtuple default values during validation by [@dmontagu](https://github.com/dmontagu) in [#7144](https://github.com/pydantic/pydantic/pull/7144)
* Update dependencies, fix pydantic-core usage, fix CI issues by [@dmontagu](https://github.com/dmontagu) in [#7150](https://github.com/pydantic/pydantic/pull/7150)
* Add mypy 1.5.0 by [@hramezani](https://github.com/hramezani) in [#7118](https://github.com/pydantic/pydantic/pull/7118)
* Handle non-json native enum values by [@adriangb](https://github.com/adriangb) in [#7056](https://github.com/pydantic/pydantic/pull/7056)
* document `round_trip` in Json type documentation by [@jc-louis](https://github.com/jc-louis) in [#7137](https://github.com/pydantic/pydantic/pull/7137)
* Relax signature checks to better support builtins and C extension functions as validators by [@adriangb](https://github.com/adriangb) in [#7101](https://github.com/pydantic/pydantic/pull/7101)
* add union_mode='left_to_right' by [@davidhewitt](https://github.com/davidhewitt) in [#7151](https://github.com/pydantic/pydantic/pull/7151)
* Include an error message hint for inherited ordering by [@yvalencia91](https://github.com/yvalencia91) in [#7124](https://github.com/pydantic/pydantic/pull/7124)
* Fix one docs link and resolve some warnings for two others by [@dmontagu](https://github.com/dmontagu) in [#7153](https://github.com/pydantic/pydantic/pull/7153)
* Include Field extra keys name in warning by [@hramezani](https://github.com/hramezani) in [#7136](https://github.com/pydantic/pydantic/pull/7136)

## V2.1.1 (2023-07-25)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.1.1)

* Skip FieldInfo merging when unnecessary by [@dmontagu](https://github.com/dmontagu) in [#6862](https://github.com/pydantic/pydantic/pull/6862)

## V2.1.0 (2023-07-25)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.1.0)

* Add `StringConstraints` for use as Annotated metadata by [@adriangb](https://github.com/adriangb) in [#6605](https://github.com/pydantic/pydantic/pull/6605)
* Try to fix intermittently failing CI by [@adriangb](https://github.com/adriangb) in [#6683](https://github.com/pydantic/pydantic/pull/6683)
* Remove redundant example of optional vs default. by [@ehiggs-deliverect](https://github.com/ehiggs-deliverect) in [#6676](https://github.com/pydantic/pydantic/pull/6676)
* Docs update by [@samuelcolvin](https://github.com/samuelcolvin) in [#6692](https://github.com/pydantic/pydantic/pull/6692)
* Remove the Validate always section in validator docs by [@adriangb](https://github.com/adriangb) in [#6679](https://github.com/pydantic/pydantic/pull/6679)
* Fix recursion error in json schema generation by [@adriangb](https://github.com/adriangb) in [#6720](https://github.com/pydantic/pydantic/pull/6720)
* Fix incorrect subclass check for secretstr by [@AlexVndnblcke](https://github.com/AlexVndnblcke) in [#6730](https://github.com/pydantic/pydantic/pull/6730)
* update pdm / pdm lockfile to 2.8.0 by [@davidhewitt](https://github.com/davidhewitt) in [#6714](https://github.com/pydantic/pydantic/pull/6714)
* unpin pdm on more CI jobs by [@davidhewitt](https://github.com/davidhewitt) in [#6755](https://github.com/pydantic/pydantic/pull/6755)
* improve source locations for auxiliary packages in docs by [@davidhewitt](https://github.com/davidhewitt) in [#6749](https://github.com/pydantic/pydantic/pull/6749)
* Assume builtins don't accept an info argument by [@adriangb](https://github.com/adriangb) in [#6754](https://github.com/pydantic/pydantic/pull/6754)
* Fix bug where calling `help(BaseModelSubclass)` raises errors by [@hramezani](https://github.com/hramezani) in [#6758](https://github.com/pydantic/pydantic/pull/6758)
* Fix mypy plugin handling of `@model_validator(mode="after")` by [@ljodal](https://github.com/ljodal) in [#6753](https://github.com/pydantic/pydantic/pull/6753)
* update pydantic-core to 2.3.1 by [@davidhewitt](https://github.com/davidhewitt) in [#6756](https://github.com/pydantic/pydantic/pull/6756)
* Mypy plugin for settings by [@hramezani](https://github.com/hramezani) in [#6760](https://github.com/pydantic/pydantic/pull/6760)
* Use `contentSchema` keyword for JSON schema by [@dmontagu](https://github.com/dmontagu) in [#6715](https://github.com/pydantic/pydantic/pull/6715)
* fast-path checking finite decimals by [@davidhewitt](https://github.com/davidhewitt) in [#6769](https://github.com/pydantic/pydantic/pull/6769)
* Docs update by [@samuelcolvin](https://github.com/samuelcolvin) in [#6771](https://github.com/pydantic/pydantic/pull/6771)
* Improve json schema doc by [@hramezani](https://github.com/hramezani) in [#6772](https://github.com/pydantic/pydantic/pull/6772)
* Update validator docs by [@adriangb](https://github.com/adriangb) in [#6695](https://github.com/pydantic/pydantic/pull/6695)
* Fix typehint for wrap validator by [@dmontagu](https://github.com/dmontagu) in [#6788](https://github.com/pydantic/pydantic/pull/6788)
* 🐛 Fix validation warning for unions of Literal and other type by [@lig](https://github.com/lig) in [#6628](https://github.com/pydantic/pydantic/pull/6628)
* Update documentation for generics support in V2 by [@tpdorsey](https://github.com/tpdorsey) in [#6685](https://github.com/pydantic/pydantic/pull/6685)
* add pydantic-core build info to `version_info()` by [@samuelcolvin](https://github.com/samuelcolvin) in [#6785](https://github.com/pydantic/pydantic/pull/6785)
* Fix pydantic dataclasses that use slots with default values by [@dmontagu](https://github.com/dmontagu) in [#6796](https://github.com/pydantic/pydantic/pull/6796)
* Fix inheritance of hash function for frozen models by [@dmontagu](https://github.com/dmontagu) in [#6789](https://github.com/pydantic/pydantic/pull/6789)
* ✨ Add `SkipJsonSchema` annotation by [@Kludex](https://github.com/Kludex) in [#6653](https://github.com/pydantic/pydantic/pull/6653)
* Error if an invalid field name is used with Field by [@dmontagu](https://github.com/dmontagu) in [#6797](https://github.com/pydantic/pydantic/pull/6797)
* Add `GenericModel` to `MOVED_IN_V2` by [@adriangb](https://github.com/adriangb) in [#6776](https://github.com/pydantic/pydantic/pull/6776)
* Remove unused code from `docs/usage/types/custom.md` by [@hramezani](https://github.com/hramezani) in [#6803](https://github.com/pydantic/pydantic/pull/6803)
* Fix `float` -> `Decimal` coercion precision loss by [@adriangb](https://github.com/adriangb) in [#6810](https://github.com/pydantic/pydantic/pull/6810)
* remove email validation from the north star benchmark by [@davidhewitt](https://github.com/davidhewitt) in [#6816](https://github.com/pydantic/pydantic/pull/6816)
* Fix link to mypy by [@progsmile](https://github.com/progsmile) in [#6824](https://github.com/pydantic/pydantic/pull/6824)
* Improve initialization hooks example by [@hramezani](https://github.com/hramezani) in [#6822](https://github.com/pydantic/pydantic/pull/6822)
* Fix default port for mongosrv DSNs by [@dmontagu](https://github.com/dmontagu) in [#6827](https://github.com/pydantic/pydantic/pull/6827)
* Improve API documentation, in particular more links between usage and API docs by [@samuelcolvin](https://github.com/samuelcolvin) in [#6780](https://github.com/pydantic/pydantic/pull/6780)
* update pydantic-core to 2.4.0 by [@davidhewitt](https://github.com/davidhewitt) in [#6831](https://github.com/pydantic/pydantic/pull/6831)
* Fix `annotated_types.MaxLen` validator for custom sequence types by [@ImogenBits](https://github.com/ImogenBits) in [#6809](https://github.com/pydantic/pydantic/pull/6809)
* Update V1 by [@hramezani](https://github.com/hramezani) in [#6833](https://github.com/pydantic/pydantic/pull/6833)
* Make it so callable JSON schema extra works by [@dmontagu](https://github.com/dmontagu) in [#6798](https://github.com/pydantic/pydantic/pull/6798)
* Fix serialization issue with `InstanceOf` by [@dmontagu](https://github.com/dmontagu) in [#6829](https://github.com/pydantic/pydantic/pull/6829)
* Add back support for `json_encoders` by [@adriangb](https://github.com/adriangb) in [#6811](https://github.com/pydantic/pydantic/pull/6811)
* Update field annotations when building the schema by [@dmontagu](https://github.com/dmontagu) in [#6838](https://github.com/pydantic/pydantic/pull/6838)
* Use `WeakValueDictionary` to fix generic memory leak by [@dmontagu](https://github.com/dmontagu) in [#6681](https://github.com/pydantic/pydantic/pull/6681)
* Add `config.defer_build` to optionally make model building lazy by [@samuelcolvin](https://github.com/samuelcolvin) in [#6823](https://github.com/pydantic/pydantic/pull/6823)
* delegate `UUID` serialization to pydantic-core by [@davidhewitt](https://github.com/davidhewitt) in [#6850](https://github.com/pydantic/pydantic/pull/6850)
* Update `json_encoders` docs by [@adriangb](https://github.com/adriangb) in [#6848](https://github.com/pydantic/pydantic/pull/6848)
* Fix error message for `staticmethod`/`classmethod` order with validate_call by [@dmontagu](https://github.com/dmontagu) in [#6686](https://github.com/pydantic/pydantic/pull/6686)
* Improve documentation for `Config` by [@samuelcolvin](https://github.com/samuelcolvin) in [#6847](https://github.com/pydantic/pydantic/pull/6847)
* Update serialization doc to mention `Field.exclude` takes priority over call-time `include/exclude` by [@hramezani](https://github.com/hramezani) in [#6851](https://github.com/pydantic/pydantic/pull/6851)
* Allow customizing core schema generation by making `GenerateSchema` public by [@adriangb](https://github.com/adriangb) in [#6737](https://github.com/pydantic/pydantic/pull/6737)

## V2.0.3 (2023-07-05)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.0.3)

* Mention PyObject (v1) moving to ImportString (v2) in migration doc by [@slafs](https://github.com/slafs) in [#6456](https://github.com/pydantic/pydantic/pull/6456)
* Fix release-tweet CI by [@Kludex](https://github.com/Kludex) in [#6461](https://github.com/pydantic/pydantic/pull/6461)
* Revise the section on required / optional / nullable fields. by [@ybressler](https://github.com/ybressler) in [#6468](https://github.com/pydantic/pydantic/pull/6468)
* Warn if a type hint is not in fact a type by [@adriangb](https://github.com/adriangb) in [#6479](https://github.com/pydantic/pydantic/pull/6479)
* Replace TransformSchema with GetPydanticSchema by [@dmontagu](https://github.com/dmontagu) in [#6484](https://github.com/pydantic/pydantic/pull/6484)
* Fix the un-hashability of various annotation types, for use in caching generic containers by [@dmontagu](https://github.com/dmontagu) in [#6480](https://github.com/pydantic/pydantic/pull/6480)
* PYD-164: Rework custom types docs by [@adriangb](https://github.com/adriangb) in [#6490](https://github.com/pydantic/pydantic/pull/6490)
* Fix ci by [@adriangb](https://github.com/adriangb) in [#6507](https://github.com/pydantic/pydantic/pull/6507)
* Fix forward ref in generic by [@adriangb](https://github.com/adriangb) in [#6511](https://github.com/pydantic/pydantic/pull/6511)
* Fix generation of serialization JSON schemas for core_schema.ChainSchema by [@dmontagu](https://github.com/dmontagu) in [#6515](https://github.com/pydantic/pydantic/pull/6515)
* Document the change in `Field.alias` behavior in Pydantic V2 by [@hramezani](https://github.com/hramezani) in [#6508](https://github.com/pydantic/pydantic/pull/6508)
* Give better error message attempting to compute the json schema of a model with undefined fields by [@dmontagu](https://github.com/dmontagu) in [#6519](https://github.com/pydantic/pydantic/pull/6519)
* Document `alias_priority` by [@tpdorsey](https://github.com/tpdorsey) in [#6520](https://github.com/pydantic/pydantic/pull/6520)
* Add redirect for types documentation by [@tpdorsey](https://github.com/tpdorsey) in [#6513](https://github.com/pydantic/pydantic/pull/6513)
* Allow updating docs without release by [@samuelcolvin](https://github.com/samuelcolvin) in [#6551](https://github.com/pydantic/pydantic/pull/6551)
* Ensure docs tests always run in the right folder by [@dmontagu](https://github.com/dmontagu) in [#6487](https://github.com/pydantic/pydantic/pull/6487)
* Defer evaluation of return type hints for serializer functions by [@dmontagu](https://github.com/dmontagu) in [#6516](https://github.com/pydantic/pydantic/pull/6516)
* Disable E501 from Ruff and rely on just Black by [@adriangb](https://github.com/adriangb) in [#6552](https://github.com/pydantic/pydantic/pull/6552)
* Update JSON Schema documentation for V2 by [@tpdorsey](https://github.com/tpdorsey) in [#6492](https://github.com/pydantic/pydantic/pull/6492)
* Add documentation of cyclic reference handling by [@dmontagu](https://github.com/dmontagu) in [#6493](https://github.com/pydantic/pydantic/pull/6493)
* Remove the need for change files by [@samuelcolvin](https://github.com/samuelcolvin) in [#6556](https://github.com/pydantic/pydantic/pull/6556)
* add "north star" benchmark by [@davidhewitt](https://github.com/davidhewitt) in [#6547](https://github.com/pydantic/pydantic/pull/6547)
* Update Dataclasses docs by [@tpdorsey](https://github.com/tpdorsey) in [#6470](https://github.com/pydantic/pydantic/pull/6470)
* ♻️ Use different error message on v1 redirects by [@Kludex](https://github.com/Kludex) in [#6595](https://github.com/pydantic/pydantic/pull/6595)
* ⬆ Upgrade `pydantic-core` to v2.2.0 by [@lig](https://github.com/lig) in [#6589](https://github.com/pydantic/pydantic/pull/6589)
* Fix serialization for IPvAny by [@dmontagu](https://github.com/dmontagu) in [#6572](https://github.com/pydantic/pydantic/pull/6572)
* Improve CI by using PDM instead of pip to install typing-extensions by [@adriangb](https://github.com/adriangb) in [#6602](https://github.com/pydantic/pydantic/pull/6602)
* Add `enum` error type docs by [@lig](https://github.com/lig) in [#6603](https://github.com/pydantic/pydantic/pull/6603)
* 🐛 Fix `max_length` for unicode strings by [@lig](https://github.com/lig) in [#6559](https://github.com/pydantic/pydantic/pull/6559)
* Add documentation for accessing features via `pydantic.v1` by [@tpdorsey](https://github.com/tpdorsey) in [#6604](https://github.com/pydantic/pydantic/pull/6604)
* Include extra when iterating over a model by [@adriangb](https://github.com/adriangb) in [#6562](https://github.com/pydantic/pydantic/pull/6562)
* Fix typing of model_validator by [@adriangb](https://github.com/adriangb) in [#6514](https://github.com/pydantic/pydantic/pull/6514)
* Touch up Decimal validator by [@adriangb](https://github.com/adriangb) in [#6327](https://github.com/pydantic/pydantic/pull/6327)
* Fix various docstrings using fixed pytest-examples by [@dmontagu](https://github.com/dmontagu) in [#6607](https://github.com/pydantic/pydantic/pull/6607)
* Handle function validators in a discriminated union by [@dmontagu](https://github.com/dmontagu) in [#6570](https://github.com/pydantic/pydantic/pull/6570)
* Review json_schema.md by [@tpdorsey](https://github.com/tpdorsey) in [#6608](https://github.com/pydantic/pydantic/pull/6608)
* Make validate_call work on basemodel methods by [@dmontagu](https://github.com/dmontagu) in [#6569](https://github.com/pydantic/pydantic/pull/6569)
* add test for big int json serde by [@davidhewitt](https://github.com/davidhewitt) in [#6614](https://github.com/pydantic/pydantic/pull/6614)
* Fix pydantic dataclass problem with dataclasses.field default_factory by [@hramezani](https://github.com/hramezani) in [#6616](https://github.com/pydantic/pydantic/pull/6616)
* Fixed mypy type inference for TypeAdapter by [@zakstucke](https://github.com/zakstucke) in [#6617](https://github.com/pydantic/pydantic/pull/6617)
* Make it work to use None as a generic parameter by [@dmontagu](https://github.com/dmontagu) in [#6609](https://github.com/pydantic/pydantic/pull/6609)
* Make it work to use `$ref` as an alias by [@dmontagu](https://github.com/dmontagu) in [#6568](https://github.com/pydantic/pydantic/pull/6568)
* add note to migration guide about changes to `AnyUrl` etc by [@davidhewitt](https://github.com/davidhewitt) in [#6618](https://github.com/pydantic/pydantic/pull/6618)
* 🐛 Support defining `json_schema_extra` on `RootModel` using `Field` by [@lig](https://github.com/lig) in [#6622](https://github.com/pydantic/pydantic/pull/6622)
* Update pre-commit to prevent commits to main branch on accident by [@dmontagu](https://github.com/dmontagu) in [#6636](https://github.com/pydantic/pydantic/pull/6636)
* Fix PDM CI for python 3.7 on MacOS/windows by [@dmontagu](https://github.com/dmontagu) in [#6627](https://github.com/pydantic/pydantic/pull/6627)
* Produce more accurate signatures for pydantic dataclasses by [@dmontagu](https://github.com/dmontagu) in [#6633](https://github.com/pydantic/pydantic/pull/6633)
* Updates to Url types for Pydantic V2 by [@tpdorsey](https://github.com/tpdorsey) in [#6638](https://github.com/pydantic/pydantic/pull/6638)
* Fix list markdown in `transform` docstring by [@StefanBRas](https://github.com/StefanBRas) in [#6649](https://github.com/pydantic/pydantic/pull/6649)
* simplify slots_dataclass construction to appease mypy by [@davidhewitt](https://github.com/davidhewitt) in [#6639](https://github.com/pydantic/pydantic/pull/6639)
* Update TypedDict schema generation docstring by [@adriangb](https://github.com/adriangb) in [#6651](https://github.com/pydantic/pydantic/pull/6651)
* Detect and lint-error for prints by [@dmontagu](https://github.com/dmontagu) in [#6655](https://github.com/pydantic/pydantic/pull/6655)
* Add xfailing test for pydantic-core PR 766 by [@dmontagu](https://github.com/dmontagu) in [#6641](https://github.com/pydantic/pydantic/pull/6641)
* Ignore unrecognized fields from dataclasses metadata by [@dmontagu](https://github.com/dmontagu) in [#6634](https://github.com/pydantic/pydantic/pull/6634)
* Make non-existent class getattr a mypy error by [@dmontagu](https://github.com/dmontagu) in [#6658](https://github.com/pydantic/pydantic/pull/6658)
* Update pydantic-core to 2.3.0 by [@hramezani](https://github.com/hramezani) in [#6648](https://github.com/pydantic/pydantic/pull/6648)
* Use OrderedDict from typing_extensions by [@dmontagu](https://github.com/dmontagu) in [#6664](https://github.com/pydantic/pydantic/pull/6664)
* Fix typehint for JSON schema extra callable by [@dmontagu](https://github.com/dmontagu) in [#6659](https://github.com/pydantic/pydantic/pull/6659)

## V2.0.2 (2023-07-05)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.0.2)

* Fix bug where round-trip pickling/unpickling a `RootModel` would change the value of `__dict__`, [#6457](https://github.com/pydantic/pydantic/pull/6457) by [@dmontagu](https://github.com/dmontagu)
* Allow single-item discriminated unions, [#6405](https://github.com/pydantic/pydantic/pull/6405) by [@dmontagu](https://github.com/dmontagu)
* Fix issue with union parsing of enums, [#6440](https://github.com/pydantic/pydantic/pull/6440) by [@dmontagu](https://github.com/dmontagu)
* Docs: Fixed `constr` documentation, renamed old `regex` to new `pattern`, [#6452](https://github.com/pydantic/pydantic/pull/6452) by [@miili](https://github.com/miili)
* Change `GenerateJsonSchema.generate_definitions` signature, [#6436](https://github.com/pydantic/pydantic/pull/6436) by [@dmontagu](https://github.com/dmontagu)

See the full changelog [here](https://github.com/pydantic/pydantic/releases/tag/v2.0.2)

## V2.0.1 (2023-07-04)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.0.1)

First patch release of Pydantic V2

* Extra fields added via `setattr` (i.e. `m.some_extra_field = 'extra_value'`)
  are added to `.model_extra` if `model_config` `extra='allowed'`. Fixed [#6333](https://github.com/pydantic/pydantic/pull/6333), [#6365](https://github.com/pydantic/pydantic/pull/6365) by [@aaraney](https://github.com/aaraney)
* Automatically unpack JSON schema '$ref' for custom types, [#6343](https://github.com/pydantic/pydantic/pull/6343) by [@adriangb](https://github.com/adriangb)
* Fix tagged unions multiple processing in submodels, [#6340](https://github.com/pydantic/pydantic/pull/6340) by [@suharnikov](https://github.com/suharnikov)

See the full changelog [here](https://github.com/pydantic/pydantic/releases/tag/v2.0.1)

## V2.0 (2023-06-30)

[GitHub release](https://github.com/pydantic/pydantic/releases/tag/v2.0)

Pydantic V2 is here! :tada:

See [this post](https://docs.pydantic.dev/2.0/blog/pydantic-v2-final/) for more details.

## v2.0b3 (2023-06-16)

Third beta pre-release of Pydantic V2

See the full changelog [here](https://github.com/pydantic/pydantic/releases/tag/v2.0b3)

## v2.0b2 (2023-06-03)

Add `from_attributes` runtime flag to `TypeAdapter.validate_python` and `BaseModel.model_validate`.

See the full changelog [here](https://github.com/pydantic/pydantic/releases/tag/v2.0b2)

## v2.0b1 (2023-06-01)

First beta pre-release of Pydantic V2

See the full changelog [here](https://github.com/pydantic/pydantic/releases/tag/v2.0b1)

## v2.0a4 (2023-05-05)

Fourth pre-release of Pydantic V2

See the full changelog [here](https://github.com/pydantic/pydantic/releases/tag/v2.0a4)

## v2.0a3 (2023-04-20)

Third pre-release of Pydantic V2

See the full changelog [here](https://github.com/pydantic/pydantic/releases/tag/v2.0a3)

## v2.0a2 (2023-04-12)

Second pre-release of Pydantic V2

See the full changelog [here](https://github.com/pydantic/pydantic/releases/tag/v2.0a2)

## v2.0a1 (2023-04-03)

First pre-release of Pydantic V2!

See [this post](https://docs.pydantic.dev/blog/pydantic-v2-alpha/) for more details.


... see [here](https://docs.pydantic.dev/changelog/#v0322-2019-08-17) for earlier changes.