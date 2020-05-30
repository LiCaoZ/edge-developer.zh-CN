---
title: Windows 运行时类型的 JavaScript 表示形式
ms.custom: ''
ms.date: 04/01/2017
ms.prod: microsoft-edge
ms.reviewer: ''
ms.suite: ''
ms.technology: windows-integration
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Runtime types [JavaScript]
- JavaScript, Windows Runtime types
ms.assetid: f4851802-8b40-4afa-ba6c-8a162a9a43cc
caps.latest.revision: 9
author: MSEdgeTeam
ms.author: msedgedevrel
manager: ''
ms.openlocfilehash: b76c28d3448b8be6fbef1fd7e23b07b2eff8d087
ms.sourcegitcommit: 6860234c25a8be863b7f29a54838e78e120dbb62
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2020
ms.locfileid: "10564588"
---
# <span data-ttu-id="d5fdc-102">Windows 运行时类型的 JavaScript 表示形式</span><span class="sxs-lookup"><span data-stu-id="d5fdc-102">JavaScript Representation of Windows Runtime Types</span></span>  

<span data-ttu-id="d5fdc-103">下表介绍了 JavaScript 表示 Windows 运行时类型的方式。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-103">The following table describes the way JavaScript represents Windows Runtime types.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="d5fdc-104">对于在 Internet Explorer 中运行的应用，Windows 运行时功能不可用。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-104">Windows Runtime features are not available for apps that run in Internet Explorer.</span></span>  

## <span data-ttu-id="d5fdc-105">JavaScript 中的 Windows 运行时类型</span><span class="sxs-lookup"><span data-stu-id="d5fdc-105">Windows Runtime Types in JavaScript</span></span>  

| <span data-ttu-id="d5fdc-106">Windows 运行时类型</span><span class="sxs-lookup"><span data-stu-id="d5fdc-106">Windows Runtime type</span></span> | <span data-ttu-id="d5fdc-107">JavaScript 表示</span><span class="sxs-lookup"><span data-stu-id="d5fdc-107">JavaScript representation</span></span> | <span data-ttu-id="d5fdc-108">描述</span><span class="sxs-lookup"><span data-stu-id="d5fdc-108">Description</span></span> |  
|:--- |:--- |:--- |  
| `UInt8` | `Number` | <span data-ttu-id="d5fdc-109">Windows 运行时 `Uint8` 是一个无符号的8位整数，表示为 JavaScript 编号。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-109">A Windows Runtime `Uint8` is an unsigned 8-bit integer, represented as a JavaScript number.</span></span>  <span data-ttu-id="d5fdc-110">JavaScript 值首先转换为 JavaScript 编号，然后 `ToUint32` 遵循该流程。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-110">A JavaScript value is first converted to a JavaScript number, and then the `ToUint32` process is followed.</span></span>  <span data-ttu-id="d5fdc-111">如果 JavaScript number 值超出 Uint8 的范围，则结果将应用模数 2 ^ 8。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-111">If the JavaScript number value is outside the range of a Uint8, the result will have modulo 2^8 applied.</span></span> |  
| `Int32` | `Number` | <span data-ttu-id="d5fdc-112">Windows 运行时 `Int32` 是一个已签名的32位整数，表示为 JavaScript 编号。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-112">A Windows Runtime `Int32` is a signed 32-bit integer, represented as a JavaScript number.</span></span>  <span data-ttu-id="d5fdc-113">JavaScript 值首先转换为 JavaScript 编号，然后 `ToInt32` 遵循该流程。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-113">A JavaScript value is first converted to a JavaScript number, and then the `ToInt32` process is followed.</span></span>  <span data-ttu-id="d5fdc-114">如果 JavaScript number 值位于 a 范围之外 `Int32` ，结果将应用模数 2 ^ 16。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-114">If the JavaScript number value is outside the range of an `Int32`, the result will have modulo 2^16 applied.</span></span> |  
| `Int64` | `Number` | <span data-ttu-id="d5fdc-115">Windows 运行时 `Int64` 是有符号的64位整数，表示为标准数字（如果它位于范围 \ [-2 ^ 53、2 ^ 53 \] 内）。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-115">A Windows Runtime `Int64` is a signed 64-bit integer, represented as a standard number if it falls within the range \[-2^53, 2^53\].</span></span>  <span data-ttu-id="d5fdc-116">如果它超出此范围，则表示为一个数字值，其中包含一个自定义后备存储，该存储保留整数数据的完整64位。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-116">If it falls outside this range, it is represented as a number value that has a custom backing store that maintains the full 64 bits of integer data.</span></span>  <span data-ttu-id="d5fdc-117">对这些自定义 Int64 数字值的所有数学运算均会将该值转换为从 \ [-2 ^ 53，2 ^ 53 \] 范围内的标准数字。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-117">All mathematical operations on these custom Int64 number values cause the value to be converted to a standard number in the range \[-2^53, 2^53\].</span></span>  <span data-ttu-id="d5fdc-118">如果该值超出此范围，则引发类型错误。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-118">If the value is outside this range, a type error is raised.</span></span>  <span data-ttu-id="d5fdc-119">此转换过程的例外是、、 `==` `===` `SameValue` 和 `RelationalComparison` 操作，它们在传递两个表示的64位值时基于完整的64位比较参数。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-119">The exceptions to this conversion process are the `==`, `===`, `SameValue`, and `RelationalComparison` operations, which compare the arguments based on the full 64 bits when passed two represented 64-bit values.</span></span>  <span data-ttu-id="d5fdc-120">如果任一参数是标准 JavaScript 编号，这些操作还会在比较之前将参数转换为 JavaScript 编号。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-120">If either argument is a standard JavaScript number, these operations also convert the argument to a JavaScript number before comparison.</span></span>  <span data-ttu-id="d5fdc-121">如果它是 Int64 值本身，则会直接分配 JavaScript 值;否则，对值应用转换的结果 `ToInteger` 将传递到 Windows 运行时。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-121">A JavaScript value is directly assigned if it is an Int64 value itself; otherwise the result of applying the `ToInteger` conversion on the value is passed to Windows Runtime.</span></span>  <span data-ttu-id="d5fdc-122">如果类型强制失败，则会返回异常。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-122">If the type coercion fails, an exception is returned.</span></span> |  
| `Uint64` | `Number` | <span data-ttu-id="d5fdc-123">Windows 运行时 `Uint64` 是一个无符号的64位整数，表示为标准数字（如果它位于范围 \ [0，2 ^ 53 \] 内）。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-123">A Windows Runtime `Uint64` is an unsigned 64-bit integer, represented as a standard number if it falls within the range \[0, 2^53\].</span></span>  <span data-ttu-id="d5fdc-124">如果它超出此范围，则表示为具有自定义后备存储的数字，该存储保留无符号整数数据的完整64位。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-124">If it falls outside this range, it is represented as a number that has a custom backing store that maintains the full 64 bits of unsigned integer data.</span></span>  <span data-ttu-id="d5fdc-125">对这些自定义 Uint64 值的所有数学运算均会将该值转换为从 \ [0，2 ^ 53 \] 范围内的标准数字。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-125">All mathematical operations on these custom Uint64 values cause the value to be converted to a standard number in the range \[0, 2^53\].</span></span>  <span data-ttu-id="d5fdc-126">如果该值超出此范围，则引发类型错误。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-126">If the value is outside this range, a type error is raised.</span></span>  <span data-ttu-id="d5fdc-127">此转换过程的例外是、、 `==` `===` `SameValue` 和 `RelationalComparison` 操作，它们在传递 2 64 位值时基于完整的64位比较参数。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-127">The exceptions to this conversion process are the `==`, `===`, `SameValue`, and `RelationalComparison` operations, which compare the arguments based on the full 64 bits when passed two 64-bit values.</span></span>  <span data-ttu-id="d5fdc-128">如果任一参数是标准 JavaScript 编号，这些操作还会在比较之前将参数转换为 JavaScript 编号。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-128">If either argument is a standard JavaScript number, these operations also convert the argument to a JavaScript number before comparison.</span></span>  <span data-ttu-id="d5fdc-129">如果它是 Uint64 值本身，则会直接分配 JavaScript 值;否则， `ToInteger` 对值应用转换的结果，然后将模数 2 ^ 52 传递到 Windows 运行时。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-129">A JavaScript value is directly assigned if it is a Uint64 value itself; otherwise, the result of applying the `ToInteger` conversion on the value, followed by taking modulo 2^52, is passed to Windows Runtime.</span></span>  <span data-ttu-id="d5fdc-130">如果类型转换失败，则会返回异常。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-130">If the type conversion fails, an exception is returned.</span></span> |  
| `Single` | `Number` | <span data-ttu-id="d5fdc-131">Windows 运行时 `Single` 是32位浮点数，表示为 JavaScript 编号，方法是将最接近的双精度值拖到单精度值中。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-131">A Windows Runtime `Single` is a 32-bit floating-point number, represented as a JavaScript number by picking the closest double-precision value to the single-precision value.</span></span>  <span data-ttu-id="d5fdc-132">JavaScript 值转换为 JavaScript 编号，然后进行范围检查，以确保该值可以用单精度32位 IEEE 754 浮点数字表示。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-132">A JavaScript value is converted to a JavaScript number and then range checked to ensure that the value can be represented in a single-precision 32-bit IEEE 754 floating-point number.</span></span>  <span data-ttu-id="d5fdc-133">如果转换或范围检查失败，则会返回封送处理错误。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-133">If the conversion or range check fails, a marshaling error is returned.</span></span> |  
| `Double` | `Number` | <span data-ttu-id="d5fdc-134">Windows 运行时 `Double` 是64位浮点数字。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-134">A Windows Runtime `Double` is a 64-bit floating-point number.</span></span>  `ToNumber` <span data-ttu-id="d5fdc-135">用于将 Windows 运行时转换 `Double` 为 JavaScript 编号。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-135">is used to convert a Windows Runtime `Double` to a JavaScript number.</span></span>  <span data-ttu-id="d5fdc-136">如果转换失败，则会返回封送处理错误。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-136">If the conversion fails, a marshaling error is returned.</span></span> |  
| `Boolean` | `Boolean` | <span data-ttu-id="d5fdc-137">Windows 运行时 `Boolean` 是8位值，其中0是零， `false` 而任何非零的值都是 `true` 以 JavaScript 的形式表示 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-137">A Windows Runtime `Boolean` is an 8-bit value where zero is `false` and any value other than zero is `true`, represented as a JavaScript `Boolean`.</span></span>  <span data-ttu-id="d5fdc-138">JavaScript 值首先被转换为 JavaScript `Boolean` `ToBoolean` 。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-138">A JavaScript value is first converted to a JavaScript `Boolean` by `ToBoolean`.</span></span>  <span data-ttu-id="d5fdc-139">这意味着，声明为的 Windows 运行时函数 `void func(BOOL);` 可以在 JavaScript 中写入 `obj.func("test");` 。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-139">This means that a Windows Runtime function declared as `void func(BOOL);` could be written in JavaScript as `obj.func("test");`.</span></span>  <span data-ttu-id="d5fdc-140">通过传递的参数调用 Windows 运行时函数 `BOOL` `TRUE` 。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-140">The Windows Runtime function is called with the `BOOL` parameter passed as `TRUE`.</span></span>  <span data-ttu-id="d5fdc-141">如果转换失败，则会返回封送处理错误。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-141">If the conversion fails, a marshaling error is returned.</span></span> |  
| `Char16` | `String` | <span data-ttu-id="d5fdc-142">Windows 运行时 `Char16` 是一个16位 Unicode 字符，表示为包含单个字符的 JavaScript 字符串。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-142">A Windows Runtime `Char16` is a 16-bit Unicode character, represented as a JavaScript string that contains a single character.</span></span>  <span data-ttu-id="d5fdc-143">JavaScript 值转换为 JavaScript 字符串 `ToString` ，然后进行检查，以确保字符串仅为一个字符长度。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-143">A JavaScript value is converted to a JavaScript string by `ToString` and then checked to ensure that the string is only a single character long.</span></span>  <span data-ttu-id="d5fdc-144">然后将单个字符作为 `Char16` 值传递。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-144">The single character is then passed as the `Char16` value.</span></span>  <span data-ttu-id="d5fdc-145">如果转换或长度检查失败，则会返回封送处理错误。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-145">If the conversion or length check fails, a marshaling error is returned.</span></span> |  
| `String` | `String` | <span data-ttu-id="d5fdc-146">Windows 运行时 `String` 是对象的不可变序列 `Char16` 。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-146">A Windows Runtime `String` is an immutable sequence of `Char16` objects.</span></span>  <span data-ttu-id="d5fdc-147">字符串表示为 JavaScript `String` 对象。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-147">Strings are represented as JavaScript `String` objects.</span></span>  <span data-ttu-id="d5fdc-148">对于和空字符串，Windows 运行时字符串不具有不同的值 `null` \ （"" \）。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-148">Windows Runtime strings do not have different values for `null` and empty string \(""\).</span></span>  `null` <span data-ttu-id="d5fdc-149">和空字符串值转换为 JavaScript 空字符串。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-149">and empty string values are converted to the JavaScript empty string.</span></span>  <span data-ttu-id="d5fdc-150">注意：当 JavaScript `null` 传递到需要字符串的 Windows 运行时参数时，它将生成字符串值 "null"，而不是 `null` 空字符串 \ （"" \ "）。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-150">Note:  When JavaScript `null` is passed to a Windows Runtime parameter that expects a string, it produces the string value "null", not `null` or the empty string \(""\).</span></span>  <span data-ttu-id="d5fdc-151">传递到 Windows 运行时的字符串应始终实例化为空字符串。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-151">Strings passed to the Windows Runtime should always be instantiated to the empty string.</span></span> |  
| `Enumeration` | `Object` | <span data-ttu-id="d5fdc-152">Windows 运行时 `Enumeration` 是具有关联的命名常量集的32位整数 \ （有符号 \）。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-152">A Windows Runtime `Enumeration` is a 32-bit integer \(signed or unsigned\) that has an associated set of named constants.</span></span>  <span data-ttu-id="d5fdc-153">在 JavaScript 中，枚举表示为一个对象，其中包含每个已命名值的只读字段。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-153">In JavaScript, an enumeration is represented as an object that contains a read-only field for each named value.</span></span>  <span data-ttu-id="d5fdc-154">枚举值转换为和的之前定义的 JavaScript 数字 `Int32` `UInt32` 。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-154">Enumeration values are converted to JavaScript numbers as defined earlier for `Int32` and `UInt32`.</span></span>  <span data-ttu-id="d5fdc-155">当 JavaScript 值转换为 Windows 运行时枚举时，将按上文所述对其进行转换、截断和范围检查。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-155">When a JavaScript value is converted to a Windows Runtime enumeration, it is converted, truncated and range checked as described earlier.</span></span>  <span data-ttu-id="d5fdc-156">但是，不对照枚举中指定的已定义命名值检查结果值。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-156">However, the resulting value is not checked against the defined named values that are specified in the enumeration.</span></span> |  
| `Structure` | `Object` | <span data-ttu-id="d5fdc-157">Windows 运行时 `Structure` 是已命名的数据字段的异类集合。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-157">A Windows Runtime `Structure` is a heterogeneous collection of named data fields.</span></span>  <span data-ttu-id="d5fdc-158">在 JavaScript 中，结构表示为一个 JavaScript 对象，该对象包含结构中每个字段的命名属性。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-158">In JavaScript, a structure is represented as a JavaScript object that contains a named property for each field in the structure.</span></span>  <span data-ttu-id="d5fdc-159">如果转换任何结构值失败，则会返回封送处理错误。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-159">If the conversion of any structure value fails, a marshaling error is returned.</span></span>  <span data-ttu-id="d5fdc-160">在 Windows 运行时结构中不具有等效项的 JavaScript 对象中的字段将被忽略。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-160">Fields in the JavaScript object that do not have equivalents in the Windows Runtime structure are ignored.</span></span>  <span data-ttu-id="d5fdc-161">注意：无法在具有关键字的 JavaScript 中实例化 Windows 运行时结构 `new` 。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-161">Note:  A Windows Runtime structure cannot be instantiated in JavaScript with the `new` keyword.</span></span> |  
| `Array` | `Array` | <span data-ttu-id="d5fdc-162">将 Windows 运行时 `Array` 转换为 JavaScript 数组。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-162">A Windows Runtime `Array` is converted to a JavaScript array.</span></span>  <span data-ttu-id="d5fdc-163">但是，Windows 运行时数组不能调整大小，因此某些 JavaScript 数组操作是不可能的。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-163">However, Windows Runtime arrays are not resizable, so some JavaScript array operations are not possible.</span></span>  <span data-ttu-id="d5fdc-164">`[[Class]]`已转换数组的 internal 属性未设置为 "array"，因为 ECMAScript 5 规范不允许这样做。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-164">The internal `[[Class]]` property of a converted array is not set to "Array" because this is not allowed by the ECMAScript 5 specification.</span></span>  <span data-ttu-id="d5fdc-165">这意味着该 `Array.isArray(v)` 返回 `false` 。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-165">This means that `Array.isArray(v)` returns `false`.</span></span>  <span data-ttu-id="d5fdc-166">JavaScript 值转换为 Windows 运行时数组，如下所示：如果值为 `null` 或 `undefined` ，则将其转换为本机 `null` 。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-166">A JavaScript value is converted to a Windows Runtime array as follows:  If the value is `null` or `undefined`, it is converted to a native `null`.</span></span>  <span data-ttu-id="d5fdc-167">如果其内部 `[[Class]]` 属性为 "Array"，则将其复制到本机数组，并传递对此数组的引用。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-167">If its internal `[[Class]]` property is "Array", it is copied to a native array and a reference to this array is passed.</span></span>  <span data-ttu-id="d5fdc-168">如果它是转换后的数组（如前面所述），则传递基础本机数组。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-168">If it is a converted array, as described previously, the underlying native array is passed.</span></span>  <span data-ttu-id="d5fdc-169">注意：将 JavaScript 数组值传递到 Windows 运行时方法会导致该数组的完整副本。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-169">Note:  Passing a JavaScript array value to a Windows Runtime method causes a full copy of the array.</span></span> |  
| <span data-ttu-id="d5fdc-170">委派 \ （函数回调 \）</span><span class="sxs-lookup"><span data-stu-id="d5fdc-170">Delegate \(function callback\)</span></span> | `Function` | <span data-ttu-id="d5fdc-171">Windows 运行时委托是对单个方法的引用。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-171">A Windows Runtime delegate is a reference to a single method.</span></span>  <span data-ttu-id="d5fdc-172">Windows 运行时委托在 JavaScript 中表示为 JavaScript `Function` ，确保在正确的线程上调用。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-172">A Windows Runtime delegate is represented in JavaScript as a JavaScript `Function`, which is guaranteed to be called on the proper thread.</span></span>  <span data-ttu-id="d5fdc-173">调用时 `Function` ，参数将转换为等效的 Windows 运行时参数类型。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-173">When the `Function` is invoked, the arguments are converted to the equivalent Windows Runtime parameter types.</span></span>  <span data-ttu-id="d5fdc-174">如果 JavaScript 参数比委托 `in` 参数少，则代理人调用失败。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-174">If there are fewer JavaScript arguments than delegate `in` parameters, the delegate call fails.</span></span>  <span data-ttu-id="d5fdc-175">如果存在的 JavaScript 参数比 `in` 委托中的参数多，则忽略额外的 javascript 参数。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-175">If there are more JavaScript arguments than there are `in` parameters in the delegate, the extra JavaScript arguments are ignored.</span></span>  <span data-ttu-id="d5fdc-176">调用委托后， `out` 参数将转换为 JavaScript 类型并返回。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-176">After the delegate is invoked, the `out` parameters are converted to JavaScript types and returned.</span></span>  <span data-ttu-id="d5fdc-177">如果将本机 JavaScript 函数对象转换为 Windows 运行时委托，则会将其包装在对应类型的 Windows 运行时委托中。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-177">If a native JavaScript function object is converted to a Windows Runtime delegate, it is wrapped in a Windows Runtime delegate of the corresponding type.</span></span>  <span data-ttu-id="d5fdc-178">调用委托时， `in` 参数将转换为 JavaScript 类型。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-178">When the delegate is invoked, the `in` parameters are converted to JavaScript types.</span></span>  <span data-ttu-id="d5fdc-179">调用委托后，返回值转换为 `out` 委托的参数。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-179">After the delegate is invoked, the return value is converted to the `out` parameters of the delegate.</span></span> |  
| <span data-ttu-id="d5fdc-180">接口</span><span class="sxs-lookup"><span data-stu-id="d5fdc-180">Interface</span></span> | `Object` | <span data-ttu-id="d5fdc-181">接口和接口组不直接在 JavaScript 中表示为对象。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-181">Interfaces and interface groups are not directly represented in JavaScript as objects.</span></span>  <span data-ttu-id="d5fdc-182">但是，接口表示为 Windows 运行时方法的参数和返回类型。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-182">However, interfaces are represented as parameter and return types of Windows Runtime methods.</span></span>  <span data-ttu-id="d5fdc-183">Windows 运行时接口实例按如下方式进行转换：</span><span class="sxs-lookup"><span data-stu-id="d5fdc-183">A Windows Runtime interface instance is converted as follows:</span></span><br /> <br /> <span data-ttu-id="d5fdc-184">1. 如果存在有效的运行时类，则将该对象表示为该类的实例。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-184">1.  If there is a valid runtime class, represent the object as an instance of that class.</span></span><br /> <span data-ttu-id="d5fdc-185">2. 如果没有有效的运行时类，则将对象表示为一个未命名的运行时类的实例，该实例仅实现该实例已知要实现的接口以及它所需的接口。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-185">2.  If there is no valid runtime class, represent the object as an instance of an unnamed runtime class that implements exactly the interface that the instance is known to implement plus its required interfaces.</span></span><br /> <br /> <span data-ttu-id="d5fdc-186">将对 JavaScript 值进行测试以确定它是否为运行时类或接口的实例。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-186">A JavaScript value is tested to determine whether it is an instance of a runtime class or an interface.</span></span>  <span data-ttu-id="d5fdc-187">如果是，并且原始 Windows 运行时值实现了该接口，则会将该对象传递到 Windows 运行时。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-187">If it is, and the original Windows Runtime value implements the interface, the object is passed to the Windows Runtime.</span></span> |  
| <span data-ttu-id="d5fdc-188">运行时类</span><span class="sxs-lookup"><span data-stu-id="d5fdc-188">Runtime classes</span></span> | `Object` | <span data-ttu-id="d5fdc-189">Windows 运行时中的对象可以是实现一个或多个接口的运行时类的实例。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-189">Objects in the Windows Runtime can be instances of runtime classes that implement one or more interfaces.</span></span>  <span data-ttu-id="d5fdc-190">Windows 运行时对象在 JavaScript 中表示为对象。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-190">Windows Runtime objects are represented in JavaScript as objects.</span></span>  <span data-ttu-id="d5fdc-191">在类的所有已实现接口上定义的方法、属性和事件的联合均表示 JavaScript 对象原型中的命名属性。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-191">The union of methods, properties, and events defined on all the implemented interfaces of the class represents the named properties in the prototype of the JavaScript object.</span></span>  <span data-ttu-id="d5fdc-192">JavaScript 使用者可以直接访问该类的任何成员。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-192">JavaScript consumers can access any member of the class directly.</span></span>  <span data-ttu-id="d5fdc-193">Windows 运行时对象具有一个原型，其中包含运行时类的所有已实现接口中的所有成员。</span><span class="sxs-lookup"><span data-stu-id="d5fdc-193">Windows Runtime objects have a prototype that contains all the members from all the implemented interfaces of the runtime class.</span></span> |  
  
## <span data-ttu-id="d5fdc-194">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d5fdc-194">See Also</span></span>  

[<span data-ttu-id="d5fdc-195">在 JavaScript 中使用 Windows 运行时</span><span class="sxs-lookup"><span data-stu-id="d5fdc-195">Using the Windows Runtime in JavaScript</span></span>][WindowsRuntimeJavascript]  

<!-- image links -->  

<!-- links -->  

[WindowsRuntimeJavascript]: /microsoft-edge/windows-runtime/using-the-windows-runtime-in-javascript "在 JavaScript 中使用 Windows 运行时"  