# The Basics

## Routing

* `RouteCollectionTest`

  * Route collection can retrieve by name
  * Route collection can get retrieve by action

* `RouteRegistererTest`

  * Middleware Fluent Registration

        ```php
            // 1.
            $this->router->middleware(['one', 'two'])->get('user', 'UserController@index');
            // 2.
            $this->router->middleware('one', 'two')->get('user', 'UserController@index');

            // 2.
            $this->router->get('user', 'UserController@index')->middleware('one', 'two');
            // 3.
            $this->router->get('user', 'UserController@index')->middleware(['one', 'two']);
        ```
  * Register resource routes
  * Register api resource routes

* `RoutingRedirectorTest`

  * Basic redirect: `$this->redirect->to('bar')`
  * Guest redirect put current url in session when method is GET
  * Guest put previous url in session when method is not GET
  * Refresh redirect
  * Back redirect to HTTP referer
  * Redirect by `action`
  * Redirect by `route`

* `RoutingRouteTest`

  * `HttpResponseException` can be caught, and content can be caught too.
  * `HEAD` method return empty content
  * NotModifiedResponse is properly returned
  * Closure Middleware
  * Alias Middleware
  * Controller Closure Middleware
  * Fluent Routing: `uses`, `middleware`
  * Middleware Groups
  * Middleware groups can reference other groups
  * Router Macro
  * Route Macro
  * Classes can be injected into routes
  * Options response are generated by default
  * `SubstituteBindings` middleware

    * Substitute bindings
    * substitute implicit bindings

  * `where` patterns
  * Router binders
  * Router model binding
  * Router Pattern
  * `is_callable`
  * Route redirect

* RoutingSortedMiddlewareTest

* RoutingUrlGeneratorTest

  * PECL delimiters
  * `strtr()` method: translate characters or replace substrings.
  * `testBasicGenerationWithRequestBaseUrlWithSubfolder`

    * `array_replace()` method.
    * `parse_url()` method.
    * `basename()` method.
    * `dirname()` method.
    * `trim()` method. Second parameter are a range of characters that we want to be stripped

  * `testBasicGenerationWithRequestBaseUrlWithSubfolderAndFileSuffix`
  * `testBasicGenerationWithRequestBaseUrlWithFileSuffix`
  * `testBasicGenerationWithPathFormatting`
  * `testUrlFormattersShouldReceiveTargetRoute`
  * `testBasicRouteGeneration`

    * `http_build_query` and `Arr::query` method to build query string.

  * `testFluentRouteNameDefinitions`
  * `testControllerRoutesWithADefaultNamespace`
  * `testControllerRoutesOutsideOfDefaultsNamespace`
  * `testRoutableInterfaceRouting`
  * `testroutableInterfaceRoutingWithSingleParameter`
  * `testRoutesMaintainRequestScheme`
  * `testHttpOnlyRoutes`
  * `testRoutesWithDomains`
  * `testRoutesWithDomainsAndPorts`
  * `testRoutesWithDomainsStripsProtocols`
  * `testHttpsRoutesWithDomains`
  * `testRoutesWithDomainsThroughProxy`
  * `testUrlGenerationForControllerRequestsPassingOfRequiredParameters`
  * `testForceRootUrl` forceRoot and forceScheme
  * `testPrevious`
  * `testRouteNotDefined`

## Middleware

* `RoutingSortedMiddlewareTest`
* `AuthorizeMiddlewareTest` for `Authorize` middleware

  * `testSimpleAbilityUnauthorized`

    1. In pipeline, parse the pipe string to get name and parameters.
    2. And then the container resolve the name of middleware.
    3. In route pipeline's `carry` method, catch the exception.

  * `testSimpleAbilityAuthorized`
  * `testSimpleAbilityWithStringParameter`
  * `testSimpleAbilityWithStringParameterFromRouteParameter`

    * `AbilityMiddleware` can get parameter from route parameter.

  * `testModelTypeUnauthorized`
  * `testModelTypeAuthorized`

    * Router `bind` method: Add a new route parameter binder
    * Router `binder` properties used in `SubstituteBindings` middleware to substitute the route bindings onto the route.

  * `testModelAuthorized`
  * `testModelInstanceAsParameter`

* `AuthenticateMiddlewareTest` for `Authenticate` middleware

  * `testDefaultUnauthenticatedThrows`

    * AuthManager

      * Custom creators: RequestGuard

    * Guard
    * Driver

      * check

  * `testDefaultUnauthenticatedThrowsWithGuards`
  * `testDefaultAuthenticatedKeepsDefaultDriver`
  * `testSecondaryAuthenticatedUpdatesDefaultDriver`
  * `testMultipleDriversUnauthenticatedThrows`
  * `testMultipleDriversUnauthenticatedThrowsGuards`
  * `testMultipleDriversAuthenticatedUpdatesDefault`

* `CacheTest` for `SetCacheHeaders` middleware

  * `testDoNotSetHeaderWhenMethodNotCacheable`

    * `SetCacheHeaders` resolve after got response instance.
    * `s-maxage`, `max-age`

  * `testDoNotSetHeaderWhenNoContent`
  * `testAddHeaders`
  * `testAddHeadersUsingArray`
  * `testGenerateEtag`
  * `testIsNotModified`
  * `testInValidOption`

* `EncryptCookiesTest` for `EncryptCookies` middleware and `AddQueuedCookiesToResponse`

  * `testSetCookieEncryption`
  * `testQueuedCookieEncryption`

    * `CookieJar`

* `VerifyCsrfTokenExceptTest` for `VerifyCsrfToken` middleware

  * `testItCanExceptPaths`
  * `testItCanExceptWildCardPaths`
  * `testItCanExceptFullUrlPaths`
  * `testItCanExceptFullUrlWildcardsPaths`

* `TransformsRequestTest` for `TransformsRequest` middleware

  * `testLowerAgeAndAddBeer`

    * Transform query and request's data to what we want.
    * `$request->get()` method: use Symfony `get` method, less use in Laravel, Use `input` instead. Because it can't resolve `json` data.

  * `testAjaxLowerAgeAndAddBeer`

    * `$request->input()` method: retrieve an item from the request
    * `data_get` method: get an item from an array or object using dot notation.

## CSRF Protection

## Controllers

## Requests

* `HttpRequestTest`
  * `testInstanceMethod`
  * `testMethodMethod`
  * `testRootMethod`: result likes `http://www.example.com`
  * `testPathMethod`: result likes `foo/bar`
  * `testDecodedPathMethod`

    * `dataProvider` annotation in PHPUnit

  * `testSegmentsProvider`
  * `testUrlMethod`: result likes `http://www.example.com/foo/bar`
  * `testFullUrlMethod`: result likes `http://www.example.com/foo/bar?a=b`

    * `$request->fullUrl()`
    * `$request->fullUrlWithQuery()`

  * `testIsMethod`
  * `testFullUrlIsMethod`
  * `testRouteIsMethod`

    * `$request->route('parameter')`: get parameter from the router

  * `testAjaxMethod`

    * Just set the header contains `X-Requested-With: XMLHttpRequest`, then the request is ajax request

  * `testPJaxMethod`

    * Set header `X-PJAX: true`

  * testSecureMethod
  * testUserAgentMethod

    * Set header `User-Agent`

  * testHasMethod: In an array using "dot" notation
  * testHasAnyMethod
  * testFilledMethod
  * testFilledAnyMethod
  * testArrayAccess
  * testAllMethod
  * testKeysMethod
  * testOnlyMethod
  * testExceptMethod
  * testPostMethod
  * testCookieMethod
  * testHasCookieMethod
  * testFileMethod
  * testHasFileMethod
  * testServerMethod
  * testMergeMethod
  * testReplaceMethod
  * testOffsetUnsetMethod
  * testHeaderMethod
  * testJSONMethod
  * testJSONEmulatingPHPBuiltInServer
  * testPrefers
  * testAllInputReturnsInputAndFiles
  * testAllInputReturnsNestedInputAndFiles
  * testAllInputReturnsInputAfterReplace
  * testAllInputWithNumericKeysReturnsInputAfterReplace
  * testInputWithEmptyFilename
  * testMultipleFileUploadWithEmptyValue
  * testOldMethodCallSession
  * testFlushMethodCallsSession
  * testExpectJson
  * testFormatReturnsAcceptableFormat
  * testFormatReturnsAcceptsJson
  * testFormatReturnsAcceptsHtml
  * testFormatReturnsAcceptsAll
  * testFormatReturnsAcceptsMultiple
  * testFormatReturnsAcceptsCharset
  * testBadAcceptHeader
  * testSessionMethod
  * testUserResolverMakesUserAvailableAsMagicProperty
  * testFingerprintMethod
  * testFingerprintWithoutRoute
  * testCreateFromBase
  * testMagicMethods
  * testHttpRequestFlashCallCallSessionFlashInputWithInputData
  * testHttpRequestFlashOnlyCallsFlashWithProperParameters
  * testHttpRequestFlashExceptCallsFlashWithProperPramaters

* `HttpMimeTest`

  * testMimeTypeFromFilenameExistsTrue
  * testMimeTypeFromFilenameExistsFalse
  * testMimeTypeFromExtensionExistsTrue
  * testMimeTypeFromExtensionExistsFalse
  * testGetAllMimeTypes
  * testSearchExtensionFromMimeType

    * `array_search()` method.

* `HttpTestingFileFactoryTest`

  * `testImagePng`
  * `testImageJpeg`

* `HttpUploadedFileTest`

  * testUploadedFileCanRetrieveContentsFromTextFile

    * `fixtures`

## Responses

* `HttpResponseTest`

  * testJsonResponseAreConvertedAndHeadersAreSet
  * testRenderablesAreRendered
  * testHeader
  * testWithCookie
  * testGetOriginalContent
  * testGetOriginalContentRetrievesTheFirstOriginalContent
  * testSetAndRetrievesStatusCode
  * testOnlyInputOnRedirect
  * testExceptInputOnRRedirect
  * testOnFlashingErrorOnRedirect
  * testSettersAndGettersOnRequest
  * testRedirectWithErrorsArrayConvertsToMessageBag
  * testWithHeaders
  * testMagicCall
  * testMagicCallException

* `HttpJsonResponseTest`

  * testSetAndRetrieveData
  * testGetOriginalContent
  * testSetAndRetrieveOptions
  * testSetAndRetrieveOptions
  * testSetAndRetrieveStatusCode
  * testInvalidArgumentExceptionOnJsonError

    * `json_last_error()` method

  * testGracefullyHandledSomeJsonErrorsWithPartialOutputError

* `HttpRedirectResponseTest`

  * testHeaderOnRedirect
  * testWithOnRedirect
  * testWithCookieOnRedirect
  * testInputOnRedirect
  * testOnlyInputOnRedirect
  * testExceptInputOnRedirect
  * testFlashingErrorOnRedirect
  * testSettersGettersOnRequest
  * testRedirectWithErrorsArrayConvertsToMessageBag
  * testMagicCall
  * testMagicCallException

## Views

* `ViewTest`

  * testDataCanBeSetOnView
  * testRenderedProperlyRendersView
  * testRenderHandlingCallbacksReturnValues

    * `is_null('') = false` and `is_null(null) = true`

  * testRenderSectionsReturnEnvironmentsSections
  * testSectionsAreNotFlushedWhenNotDoneRendering
  * testViewNestBindsASubView
  * testViewAcceptsArrayableImplementations
  * testViewGettersSetters
  * testViewArrayAccess
  * testViewConstructedWithObjectData

    * Object transform to array: `(array) $objectA`

  * testBadMethod
  * testViewGatherDataWithRenderable
  * testViewRenderSections
  * testWithErrors

## URLGeneration

* `RoutingUrlGeneratorTest`

  * ...

* `UrlSigningTest`

  * test_signing_url
  * test_temporary_signed_urls
  * test_signed_url_with_url_without_signature_parameter
  * test_signed_middleware
  * test_signed_middleware_with_invalid_url
  * test_signed_middleware_with_routable_middleware

## HTTP Session

* `SessionStoreTest`

  * testSessionIsLoadedFromHandler
  * testSessionMigration
  * testSessionRegeneration
  * testCantSetInvalidId
  * testSessionInvalidate
  * testSessionIsProperlySaved

    * `push` and `put`: `push` is for array items, and `put` is for key / value pair.

  * testOldInputFlashing
  * testDataFlashing
  * testDataFlashingNow
  * testDataMergeNewFlashes
  * testReflash
  * testReflashWithNow
  * testReplace
  * testRemove
  * testClear
  * testIncrement
  * testDecrement
  * testHasOldInputWithoutKey
  * testHandlerNeedsRequest
  * testToken
  * testRegenerateToken
  * testName
  * testKeyExists
  * testRememberMethodCallsPutAndReturnsDefault

* EncryptedSessionStoreTest

  * testSessionIsProperlyEncrypted

## Validation

* `ValidationValidatorTest`

  * testSometimesWorksOnNestedArrays

    * Array destructor: since php 7.1

  * testAfterCallbacksAreCalledWithValidatorInstance
  * testSomeTimesWorksOnArrays
  * testValidateThrowsOnFail
  * testValidateDoesntThrowOnPass
  * testHasFailedValidationRules
  * testFailingOnce
  * testHasNotFailedValidationRules
  * testSometimesCanSkipRequireRules
  * testInvalitableRulesReturnsValid
  * testValidEmptyStringsAlwaysPasses
  * testEmptyExistingAttributesAreValidated
  * testNullable
  * testNullableMakesNoDifferenceIfImplicitRuleExists
  * testProperLanguageLineIsSet
  * testCustomReplacersAreCalled
  * testClassBasedCustomReplacers
  * testNestedAttributesAreReplacedInDimensions
  * testAttributeNamesAreReplaced
  * testAttributeNamesAreReplacedInArrays
  * testInputIsReplaced

    * `is_scalar`

  * testDisplayableValuesAreReplaced
  * testDisplayableAttributesAreReplacedInCustomReplacers
  * testCustomValidationLinesAreRespected
  * testCustomValidationLinesAreRespectedWithAsterisks
  * testValidationDotCustomDotAnythingCanBeTranslated
  * testInlineValidationMessagesAreRespected
  * testInlineValidationMessagesAreRespectedWithAsterisks
  * testIfRulesAreSuccessfullyAdded
  * testValidateArray
  * testValidateFilled
  * testValidationStopsAtFailedPresenceCheck
  * testValidatePresent
  * testValidateRequired
  * testValidateRequiredWith
  * testRequiredWithAll
  * testValidateRequiredWithout
  * testRequiredWithoutMultiple
  * testRequiredWithoutAll
  * testRequiredIf
  * testRequiredUnless
  * testFailedFileUploads
  * testValidateInArray
  * testValidConfirmed
  * testValidSame
  * testValidDifferent
  * testGreaterThan
  * testLessThan
  * testGreaterThanOrEqual
  * testLessThanOrEqual
  * testValidateAccepted
  * testValidateString
  * testValidateJson
  * testValidateBoolean
  * testValidateBool
  * testValidateNumeric
  * testValidateInteger
  * testValidateInt
  * testValidateDigits
  * testValidateSize
  * testValidateBetween
  * testValidateMin
  * testValidateMax
  * testProperMessagesAreReturnedForSizes
  * testValidateGtPlaceHolderIsReplacedProperly
  * testValidateLtPlaceHolderIsReplacedProperly
  * testValidateGtePlaceHolderIsReplacedProperly
  * testValidateLtePlaceHolderIsReplacedProperly
  * testValidateIn
  * testValidateNotIn
  * testValidateDistinct
  * testValidateUnique
  * testValidateUniqueAndExistsSendsCorrectFieldNameToDBWithArrays
  * testValidationExists
  * testValidationExistsIsNotCalledUnnecessarialy
  * testValidIP
  * testValidEmail
  * testValidUrlWithValidUrls
  * testValidUrlWithInvalidUrls
  * testValidateActiveUrl

    * `dns_get_record()`

  * testValidImage
  * testValidImageDoesNotAllowPhpExtensionsOnImageMime
  * testValidateImageDimensions
  * testValidatePhpMimeTypes
  * testValidateMime
  * testValidateMimeEnforcesPhpCheck
  * testValidateFile
  * testEmptyRulesSkipped
  * testAlternativeFormat
  * testValidateAlpha
  * testValidateAlphaNum
  * testValidateAlphaDash
  * testValidateTimezone
  * testValidateRegex
  * testValidateNotRegex
  * testValidateDateAndFormat
  * testDateEquals
  * testDateEqualsRespectsCarbonTestNowWhenParameterIsRelative
  * testBeforeAndAfter
  * testBeforeAndAfterWithFormat
  * testWeakBeforeAndAfter
  * testCustomValidators
  * testClassBasedCustomValidators
  * testClassBasedCustomValidatorsUsingConventionalMethod
  * testCustomImplicitValidators
  * testCustomDependentValidators
  * testExceptionThrownOnIncorrectParameterCount
  * testValidateImplicitEachWithAsterisks
  * testSometimesOnArraysImplicitRules
  * testValidateImplicitEachWithAsterisksForRequiredNoneExistingKey
  * testsParsingArrayKeysWithDot
  * testCoveringEmptyKeys
  * testImplicitEachWithAsterisksWithArrayValues
  * testValidNestedArrayWithCommonParentChildKey
  * testValidateNestedArrayWithNonNumericKeys
  * testValidateImplicitEachWithAsterisksConfirmed
  * testValidateImplicitEachWithAsterisksDifferent
  * testValidateImplicitEachWithAsterisksSame
  * testValidateImplicitEachWithAsterisksRequired
  * testValidateImplicitEachWithAsterisksRequiredIf
  * testValidateImplicitEachWithAsterisksRequiredUnless
  * testValidateImplicitEachWithAsterisksRequiredWith
  * testValidateImplicitEachWithAsterisksRequiredWithAll
  * testValidateImplicitEachWithAsterisksRequiredWithout
  * testValidateImplicitEachWithAsterisksRequiredWithoutAll
  * testValidateImplicitEachWithAsterisksBeforeAndAfter
  * testGetLeadingExplicitAttributePath
  * testExtractDateFromPath
  * testUsingSettersWithImplicitRules
  * testInvalidMethod
  * testValidMethod
  * testMultipleFileUploads
  * testFileUploads
  * testCustomValidationObject
  * testImplicitCustomValidationObjects
  * testValidateReturnsValidatedData
  * testValidateReturnsValidatedDataNestedRules
  * testValidateReturnsValidatedDataNestedChildRules
  * testValidateReturnsValidatedDataNestedArrayRules

* `ValidationAddFailureTest`

  * testAddFailureExists
  * testAddFailureIsFunctional

* ValidationDatabasePresenceVerifierTest

  * testBasicCount
  * testBasicCountWithClosures

* ValidationDimensionsRuleTest

  * testItCorrectlyFormatsAStringVersionOfTheRule

* ValidationExistsRuleTest

  * testItCorrectlyFormatsAStringVersionOfTheRule
  * testItChoosesValidRecordsUsingWhereInRule
  * testItChoosesValidRecordsUsingWhereNotInRule
  * testItChoosesValidRecordsUsingWhereNotInAndWhereNotInTogether

* ValidationFactoryTest

  * testMakeMethodCreatesValidValidator
  * testValidateCallsValidateOnTheValidator
  * testCustomResolverIsCalled
  * testValidateMethodCanBeCalledPublicly

* ValidationInRuleTest

  * testItCorrectlyFormatsAStringVersionOfTheRule

* ValidationNotInRuleTest

  * testItCorrectlyFormatsAStringVersionOfTheRule

* ValidationRequiredIfTest

  * testItClosureReturnsFormatsAStringVersionOfTheRule

* ValidationRuleTest

  * testMacroable

* ValidationUniqueRuleTest

  * testItCorrectlyFormatsAStringVersionOfTheRule

## Error Handling

* FoundationExceptionsHandlerTest

  * testHandlerReportsExceptionAsContext
  * testReturnsJsonWithStackTraceWhenAjaxRequestAndDebugTrue
  * testResponseCustomResponseWhenExceptionImplementsResponsable
  * testReturnsJsonWithoutStackTraceWhenAjaxRequestAndDebugFalseAndExceptionMessageIsMarked
  * testReturnsJsonWithoutStackTraceWhenAjaxRequestAndDebugFalseAndHttpExceptionIsShown
  * testReturnsJsonnWithoutStackTraceWhenAjaxRequestAndDebugFalseAndAccessDeniedHttpExceptionErrorIsShown

## Logging

* LogLoggerTest

  * testMethodsPassErrorAdditionsToMonolog
  * testLoggerFiresEventsDispatcher
  * testListenShortcutFailsWithNoDispatcher
  * testListenShortcut

* LogManagerTest

  * testLogManagerCachesLoggerInstances
  * testLogManagerCreatesConfigureMonologHandler
  * testLogManagerCreatesMonologHandlerWithConfiguredFormatter
