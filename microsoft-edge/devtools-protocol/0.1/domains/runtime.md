---
description: 对运行时域的引用。 运行时域通过远程计算和镜像对象公开 JavaScript 运行时。 计算结果以镜像对象的形式返回，该对象公开可用于进一步对象引用的对象类型、字符串表示形式和唯一标识符。 原始对象将保留在内存中，除非它们被显式释放。
title: 运行时域-DevTools 协议版本0。1
author: pelavall
ms.author: pelavall
ms.date: 12/15/2017
ms.topic: reference
ms.prod: microsoft-edge
ms.custom: seodec18
ms.openlocfilehash: 33bc98b272aaa8831e908207b97ea7d3d0842976
ms.sourcegitcommit: 6860234c25a8be863b7f29a54838e78e120dbb62
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2020
ms.locfileid: "10563421"
---
# <span data-ttu-id="2a844-106">运行时</span><span class="sxs-lookup"><span data-stu-id="2a844-106">Runtime</span></span>
<span data-ttu-id="2a844-107">运行时域通过远程计算和镜像对象公开 JavaScript 运行时。</span><span class="sxs-lookup"><span data-stu-id="2a844-107">Runtime domain exposes JavaScript runtime by means of remote evaluation and mirror objects.</span></span> <span data-ttu-id="2a844-108">计算结果以镜像对象的形式返回，该对象公开可用于进一步对象引用的对象类型、字符串表示形式和唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="2a844-108">Evaluation results are returned as mirror object that expose object type, string representation and unique identifier that can be used for further object reference.</span></span> <span data-ttu-id="2a844-109">原始对象将保留在内存中，除非它们被显式释放。</span><span class="sxs-lookup"><span data-stu-id="2a844-109">Original objects are maintained in memory unless they are either explicitly released.</span></span>

| | |
|-|-|
| [**<span data-ttu-id="2a844-110">方法</span><span class="sxs-lookup"><span data-stu-id="2a844-110">Methods</span></span>**](#methods) | <span data-ttu-id="2a844-111">[enable](#enable)、 [disable](#disable)、[求值](#evaluate)、 [callFunctionOn](#callfunctionon)、 [getProperties](#getproperties)</span><span class="sxs-lookup"><span data-stu-id="2a844-111">[enable](#enable), [disable](#disable), [evaluate](#evaluate), [callFunctionOn](#callfunctionon), [getProperties](#getproperties)</span></span> |
| [**<span data-ttu-id="2a844-112">事件</span><span class="sxs-lookup"><span data-stu-id="2a844-112">Events</span></span>**](#events) | <span data-ttu-id="2a844-113">[executionContextsCleared](#executioncontextscleared)、 [exceptionThrown](#exceptionthrown)</span><span class="sxs-lookup"><span data-stu-id="2a844-113">[executionContextsCleared](#executioncontextscleared), [exceptionThrown](#exceptionthrown)</span></span> |
| [**<span data-ttu-id="2a844-114">类型</span><span class="sxs-lookup"><span data-stu-id="2a844-114">Types</span></span>**](#types) | <span data-ttu-id="2a844-115">[ScriptId](#scriptid)、 [RemoteObjectId](#remoteobjectid)、 [UnserializableValue](#unserializablevalue)、 [RemoteObject](#remoteobject)、 [PropertyDescriptor](#propertydescriptor)、 [CallArgument](#callargument)、 [ExecutionContextId](#executioncontextid)、 [ExceptionDetails](#exceptiondetails)、 [Timestamp](#timestamp)、 [CallFrame](#callframe)、 [StackTrace](#stacktrace)</span><span class="sxs-lookup"><span data-stu-id="2a844-115">[ScriptId](#scriptid), [RemoteObjectId](#remoteobjectid), [UnserializableValue](#unserializablevalue), [RemoteObject](#remoteobject), [PropertyDescriptor](#propertydescriptor), [CallArgument](#callargument), [ExecutionContextId](#executioncontextid), [ExceptionDetails](#exceptiondetails), [Timestamp](#timestamp), [CallFrame](#callframe), [StackTrace](#stacktrace)</span></span> |
## <span data-ttu-id="2a844-116">方法</span><span class="sxs-lookup"><span data-stu-id="2a844-116">Methods</span></span>

### <span data-ttu-id="2a844-117">“启用”</span><span class="sxs-lookup"><span data-stu-id="2a844-117">enable</span></span>
<span data-ttu-id="2a844-118">启用 <code>executionContextsCleared</code> 事件报告。</span><span class="sxs-lookup"><span data-stu-id="2a844-118">Enables reporting of the <code>executionContextsCleared</code> event.</span></span>


---

### <span data-ttu-id="2a844-119">“禁用”</span><span class="sxs-lookup"><span data-stu-id="2a844-119">disable</span></span>
<span data-ttu-id="2a844-120">禁用 <code>executionContextsCleared</code> 事件报告。</span><span class="sxs-lookup"><span data-stu-id="2a844-120">Disables reporting of the <code>executionContextsCleared</code> event.</span></span>


---

### <span data-ttu-id="2a844-121">评判</span><span class="sxs-lookup"><span data-stu-id="2a844-121">evaluate</span></span>
<span data-ttu-id="2a844-122">计算全局对象上的表达式。</span><span class="sxs-lookup"><span data-stu-id="2a844-122">Evaluates expression on global object.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="2a844-123">参数</span><span class="sxs-lookup"><span data-stu-id="2a844-123">Parameters</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="2a844-124">表达</span><span class="sxs-lookup"><span data-stu-id="2a844-124">expression</span></span></td>
            <td><code class="flyout">string</code></td>
            <td><span data-ttu-id="2a844-125">要计算的表达式。</span><span class="sxs-lookup"><span data-stu-id="2a844-125">Expression to evaluate.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-126">silent</span><span class="sxs-lookup"><span data-stu-id="2a844-126">silent</span></span> <br/> <i><span data-ttu-id="2a844-127">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-127">optional</span></span></i></td>
            <td><code class="flyout">boolean</code></td>
            <td><span data-ttu-id="2a844-128">在计算期间引发的静默模式异常不会报告，并且不会暂停执行。</span><span class="sxs-lookup"><span data-stu-id="2a844-128">In silent mode exceptions thrown during evaluation are not reported and do not pause execution.</span></span> <span data-ttu-id="2a844-129">重写 <code>setPauseOnException</code> 状态。</span><span class="sxs-lookup"><span data-stu-id="2a844-129">Overrides <code>setPauseOnException</code> state.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-130">contextId</span><span class="sxs-lookup"><span data-stu-id="2a844-130">contextId</span></span> <br/> <i><span data-ttu-id="2a844-131">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-131">optional</span></span></i></td>
            <td><a href="#executioncontextid"><code class="flyout">ExecutionContextId</code></a></td>
            <td><span data-ttu-id="2a844-132">指定要在其中执行计算的执行上下文。</span><span class="sxs-lookup"><span data-stu-id="2a844-132">Specifies in which execution context to perform evaluation.</span></span> <span data-ttu-id="2a844-133">如果省略该参数，将在已检查页面的上下文中执行计算。</span><span class="sxs-lookup"><span data-stu-id="2a844-133">If the parameter is omitted the evaluation will be performed in the context of the inspected page.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-134">returnByValue</span><span class="sxs-lookup"><span data-stu-id="2a844-134">returnByValue</span></span> <br/> <i><span data-ttu-id="2a844-135">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-135">optional</span></span></i></td>
            <td><code class="flyout">boolean</code></td>
            <td><span data-ttu-id="2a844-136">结果是否应为应由 value 发送的 JSON 对象。</span><span class="sxs-lookup"><span data-stu-id="2a844-136">Whether the result is expected to be a JSON object that should be sent by value.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-137">awaitPromise</span><span class="sxs-lookup"><span data-stu-id="2a844-137">awaitPromise</span></span> <br/> <i><span data-ttu-id="2a844-138">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-138">optional</span></span></i></td>
            <td><code class="flyout">boolean</code></td>
            <td><span data-ttu-id="2a844-139"><code>await</code>在解决已完成的承诺后，是否应执行结果值和返回。</span><span class="sxs-lookup"><span data-stu-id="2a844-139">Whether execution should <code>await</code> for resulting value and return once awaited promise is resolved.</span></span></td>
        </tr>
    </tbody>
</table>
<table>
    <thead>
        <tr>
            <th><span data-ttu-id="2a844-140">返回</span><span class="sxs-lookup"><span data-stu-id="2a844-140">Returns</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="2a844-141">结果</span><span class="sxs-lookup"><span data-stu-id="2a844-141">result</span></span></td>
            <td><a href="#remoteobject"><code class="flyout">RemoteObject</code></a></td>
            <td><span data-ttu-id="2a844-142">评估结果。</span><span class="sxs-lookup"><span data-stu-id="2a844-142">Evaluation result.</span></span></td>
        </tr>
    </tbody>
</table>

---

### <span data-ttu-id="2a844-143">callFunctionOn</span><span class="sxs-lookup"><span data-stu-id="2a844-143">callFunctionOn</span></span>
<span data-ttu-id="2a844-144">调用具有给定对象的给定声明的函数。</span><span class="sxs-lookup"><span data-stu-id="2a844-144">Calls function with given declaration on the given object.</span></span> <span data-ttu-id="2a844-145">结果的对象组继承自目标对象。</span><span class="sxs-lookup"><span data-stu-id="2a844-145">Object group of the result is inherited from the target object.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="2a844-146">参数</span><span class="sxs-lookup"><span data-stu-id="2a844-146">Parameters</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="2a844-147">functionDeclaration</span><span class="sxs-lookup"><span data-stu-id="2a844-147">functionDeclaration</span></span></td>
            <td><code class="flyout">string</code></td>
            <td><span data-ttu-id="2a844-148">要调用的函数的声明。</span><span class="sxs-lookup"><span data-stu-id="2a844-148">Declaration of the function to call.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-149">objectId</span><span class="sxs-lookup"><span data-stu-id="2a844-149">objectId</span></span> <br/> <i><span data-ttu-id="2a844-150">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-150">optional</span></span></i></td>
            <td><a href="#remoteobjectid"><code class="flyout">RemoteObjectId</code></a></td>
            <td><span data-ttu-id="2a844-151">要在其上调用函数的对象的标识符。</span><span class="sxs-lookup"><span data-stu-id="2a844-151">Identifier of the object to call function on.</span></span> <span data-ttu-id="2a844-152">应指定 "objectId" 或 "executionContextId"。</span><span class="sxs-lookup"><span data-stu-id="2a844-152">Either objectId or executionContextId should be specified.</span></span>  <span data-ttu-id="2a844-153">objectId 必须来自 Runtime。求值（）函数。</span><span class="sxs-lookup"><span data-stu-id="2a844-153">objectId must be from the Runtime.evaluate() function.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-154">arguments</span><span class="sxs-lookup"><span data-stu-id="2a844-154">arguments</span></span> <br/> <i><span data-ttu-id="2a844-155">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-155">optional</span></span></i></td>
            <td><a href="#callargument"><code class="flyout">CallArgument[]</code></a></td>
            <td><span data-ttu-id="2a844-156">调用参数。</span><span class="sxs-lookup"><span data-stu-id="2a844-156">Call arguments.</span></span> <span data-ttu-id="2a844-157">所有调用参数都必须属于与目标对象相同的 JavaScript world。</span><span class="sxs-lookup"><span data-stu-id="2a844-157">All call arguments must belong to the same JavaScript world as the target object.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-158">silent</span><span class="sxs-lookup"><span data-stu-id="2a844-158">silent</span></span> <br/> <i><span data-ttu-id="2a844-159">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-159">optional</span></span></i></td>
            <td><code class="flyout">boolean</code></td>
            <td><span data-ttu-id="2a844-160">在计算期间引发的静默模式异常不会报告，并且不会暂停执行。</span><span class="sxs-lookup"><span data-stu-id="2a844-160">In silent mode exceptions thrown during evaluation are not reported and do not pause execution.</span></span> <span data-ttu-id="2a844-161">重写 <code>setPauseOnException</code> 状态。</span><span class="sxs-lookup"><span data-stu-id="2a844-161">Overrides <code>setPauseOnException</code> state.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-162">returnByValue</span><span class="sxs-lookup"><span data-stu-id="2a844-162">returnByValue</span></span> <br/> <i><span data-ttu-id="2a844-163">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-163">optional</span></span></i></td>
            <td><code class="flyout">boolean</code></td>
            <td><span data-ttu-id="2a844-164">结果是否应为应由 value 发送的 JSON 对象。</span><span class="sxs-lookup"><span data-stu-id="2a844-164">Whether the result is expected to be a JSON object which should be sent by value.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-165">awaitPromise</span><span class="sxs-lookup"><span data-stu-id="2a844-165">awaitPromise</span></span> <br/> <i><span data-ttu-id="2a844-166">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-166">optional</span></span></i></td>
            <td><code class="flyout">boolean</code></td>
            <td><span data-ttu-id="2a844-167"><code>await</code>在解决已完成的承诺后，是否应执行结果值和返回。</span><span class="sxs-lookup"><span data-stu-id="2a844-167">Whether execution should <code>await</code> for resulting value and return once awaited promise is resolved.</span></span></td>
        </tr>
    </tbody>
</table>
<table>
    <thead>
        <tr>
            <th><span data-ttu-id="2a844-168">返回</span><span class="sxs-lookup"><span data-stu-id="2a844-168">Returns</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="2a844-169">结果</span><span class="sxs-lookup"><span data-stu-id="2a844-169">result</span></span></td>
            <td><a href="#remoteobject"><code class="flyout">RemoteObject</code></a></td>
            <td><span data-ttu-id="2a844-170">呼叫结果。</span><span class="sxs-lookup"><span data-stu-id="2a844-170">Call result.</span></span></td>
        </tr>
    </tbody>
</table>

---

### <span data-ttu-id="2a844-171">getProperties</span><span class="sxs-lookup"><span data-stu-id="2a844-171">getProperties</span></span>
<span data-ttu-id="2a844-172">返回给定对象的属性。</span><span class="sxs-lookup"><span data-stu-id="2a844-172">Returns properties of a given object.</span></span> <span data-ttu-id="2a844-173">结果的对象组继承自目标对象。</span><span class="sxs-lookup"><span data-stu-id="2a844-173">Object group of the result is inherited from the target object.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="2a844-174">参数</span><span class="sxs-lookup"><span data-stu-id="2a844-174">Parameters</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="2a844-175">objectId</span><span class="sxs-lookup"><span data-stu-id="2a844-175">objectId</span></span></td>
            <td><a href="#remoteobjectid"><code class="flyout">RemoteObjectId</code></a></td>
            <td><span data-ttu-id="2a844-176">要为其返回属性的对象的标识符。</span><span class="sxs-lookup"><span data-stu-id="2a844-176">Identifier of the object to return properties for.</span></span>  <span data-ttu-id="2a844-177">objectId 必须来自 evaluateOnCallFrame （）函数。</span><span class="sxs-lookup"><span data-stu-id="2a844-177">objectId must be from the Debugger.evaluateOnCallFrame() function.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-178">ownProperties</span><span class="sxs-lookup"><span data-stu-id="2a844-178">ownProperties</span></span> <br/> <i><span data-ttu-id="2a844-179">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-179">optional</span></span></i></td>
            <td><code class="flyout">boolean</code></td>
            <td><span data-ttu-id="2a844-180">如果为 true，则返回仅属于元素本身的属性，而不是其原型链。</span><span class="sxs-lookup"><span data-stu-id="2a844-180">If true, returns properties belonging only to the element itself, not to its prototype chain.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-181">accessorPropertiesOnly</span><span class="sxs-lookup"><span data-stu-id="2a844-181">accessorPropertiesOnly</span></span> <br/> <i><span data-ttu-id="2a844-182">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-182">optional</span></span></i></td>
            <td><code class="flyout">boolean</code></td>
            <td><span><b><span data-ttu-id="2a844-183">实验.</span><span class="sxs-lookup"><span data-stu-id="2a844-183">Experimental.</span></span> </b></span><span data-ttu-id="2a844-184">如果为 true，则仅返回访问器属性（具有 getter/setter）;内部属性也不会返回。</span><span class="sxs-lookup"><span data-stu-id="2a844-184">If true, returns accessor properties (with getter/setter) only; internal properties are not returned either.</span></span></td>
        </tr>
    </tbody>
</table>
<table>
    <thead>
        <tr>
            <th><span data-ttu-id="2a844-185">返回</span><span class="sxs-lookup"><span data-stu-id="2a844-185">Returns</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="2a844-186">结果</span><span class="sxs-lookup"><span data-stu-id="2a844-186">result</span></span></td>
            <td><a href="#propertydescriptor"><code class="flyout">PropertyDescriptor[]</code></a></td>
            <td><span data-ttu-id="2a844-187">对象属性。</span><span class="sxs-lookup"><span data-stu-id="2a844-187">Object properties.</span></span></td>
        </tr>
    </tbody>
</table>

---

## <span data-ttu-id="2a844-188">事件</span><span class="sxs-lookup"><span data-stu-id="2a844-188">Events</span></span>

### <span data-ttu-id="2a844-189">executionContextsCleared</span><span class="sxs-lookup"><span data-stu-id="2a844-189">executionContextsCleared</span></span>
<span data-ttu-id="2a844-190">在浏览器中清除所有 executionContexts 时发出</span><span class="sxs-lookup"><span data-stu-id="2a844-190">Issued when all executionContexts were cleared in browser</span></span>


---

### <span data-ttu-id="2a844-191">exceptionThrown</span><span class="sxs-lookup"><span data-stu-id="2a844-191">exceptionThrown</span></span>
<span data-ttu-id="2a844-192">当异常引发且未经处理时发出。</span><span class="sxs-lookup"><span data-stu-id="2a844-192">Issued when exception was thrown and unhandled.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="2a844-193">参数</span><span class="sxs-lookup"><span data-stu-id="2a844-193">Parameters</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="2a844-194">icmp</span><span class="sxs-lookup"><span data-stu-id="2a844-194">timestamp</span></span></td>
            <td><a href="#timestamp"><code class="flyout">Timestamp</code></a></td>
            <td><span data-ttu-id="2a844-195">异常的时间戳。</span><span class="sxs-lookup"><span data-stu-id="2a844-195">Timestamp of the exception.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-196">exceptionDetails</span><span class="sxs-lookup"><span data-stu-id="2a844-196">exceptionDetails</span></span></td>
            <td><a href="#exceptiondetails"><code class="flyout">ExceptionDetails</code></a></td>
            <td></td>
        </tr>
    </tbody>
</table>

---

## <span data-ttu-id="2a844-197">类型</span><span class="sxs-lookup"><span data-stu-id="2a844-197">Types</span></span>

### <a name="scriptid"></a> <span data-ttu-id="2a844-198">ScriptId</span><span class="sxs-lookup"><span data-stu-id="2a844-198">ScriptId</span></span> `string`

<span data-ttu-id="2a844-199">唯一的脚本标识符。</span><span class="sxs-lookup"><span data-stu-id="2a844-199">Unique script identifier.</span></span>


---

### <a name="remoteobjectid"></a> <span data-ttu-id="2a844-200">RemoteObjectId</span><span class="sxs-lookup"><span data-stu-id="2a844-200">RemoteObjectId</span></span> `string`

<span data-ttu-id="2a844-201">唯一的对象标识符。</span><span class="sxs-lookup"><span data-stu-id="2a844-201">Unique object identifier.</span></span>


---

### <a name="unserializablevalue"></a> <span data-ttu-id="2a844-202">UnserializableValue</span><span class="sxs-lookup"><span data-stu-id="2a844-202">UnserializableValue</span></span> `string`

<span data-ttu-id="2a844-203">基元值，不能是 JSON-stringified。</span><span class="sxs-lookup"><span data-stu-id="2a844-203">Primitive value which cannot be JSON-stringified.</span></span>

##### <span data-ttu-id="2a844-204">允许值</span><span class="sxs-lookup"><span data-stu-id="2a844-204">Allowed Values</span></span>
<span data-ttu-id="2a844-205">无穷大、NaN、-无穷大、-0</span><span class="sxs-lookup"><span data-stu-id="2a844-205">Infinity, NaN, -Infinity, -0</span></span>

---

### <a name="remoteobject"></a> <span data-ttu-id="2a844-206">RemoteObject</span><span class="sxs-lookup"><span data-stu-id="2a844-206">RemoteObject</span></span> `object`

<span data-ttu-id="2a844-207">镜像对象引用原始 JavaScript 对象。</span><span class="sxs-lookup"><span data-stu-id="2a844-207">Mirror object referencing original JavaScript object.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="2a844-208">属性</span><span class="sxs-lookup"><span data-stu-id="2a844-208">Properties</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="2a844-209">类型</span><span class="sxs-lookup"><span data-stu-id="2a844-209">type</span></span></td>
            <td><code class="flyout">string</code> <br/> <i><span data-ttu-id="2a844-210">允许的值： object、函数、undefined、string、number、boolean、符号</span><span class="sxs-lookup"><span data-stu-id="2a844-210">Allowed values: object, function, undefined, string, number, boolean, symbol</span></span></i></td>
            <td><span data-ttu-id="2a844-211">对象类型。</span><span class="sxs-lookup"><span data-stu-id="2a844-211">Object type.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-212">子类型</span><span class="sxs-lookup"><span data-stu-id="2a844-212">subtype</span></span> <br/> <i><span data-ttu-id="2a844-213">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-213">optional</span></span></i></td>
            <td><code class="flyout">string</code> <br/> <i><span data-ttu-id="2a844-214">允许的值： null、错误、承诺</span><span class="sxs-lookup"><span data-stu-id="2a844-214">Allowed values: null, error, promise</span></span></i></td>
            <td><span data-ttu-id="2a844-215">Object 子类型提示。</span><span class="sxs-lookup"><span data-stu-id="2a844-215">Object subtype hint.</span></span> <span data-ttu-id="2a844-216">仅为 <code>object</code> 类型值指定。</span><span class="sxs-lookup"><span data-stu-id="2a844-216">Specified for <code>object</code> type values only.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-217">缺少</span><span class="sxs-lookup"><span data-stu-id="2a844-217">className</span></span> <br/> <i><span data-ttu-id="2a844-218">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-218">optional</span></span></i></td>
            <td><code class="flyout">string</code></td>
            <td><span data-ttu-id="2a844-219">对象类（构造函数）名称。</span><span class="sxs-lookup"><span data-stu-id="2a844-219">Object class (constructor) name.</span></span> <span data-ttu-id="2a844-220">仅为 <code>object</code> 类型值指定。</span><span class="sxs-lookup"><span data-stu-id="2a844-220">Specified for <code>object</code> type values only.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-221">值</span><span class="sxs-lookup"><span data-stu-id="2a844-221">value</span></span> <br/> <i><span data-ttu-id="2a844-222">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-222">optional</span></span></i></td>
            <td><code class="flyout">any</code></td>
            <td><span data-ttu-id="2a844-223">在基元值或 JSON 值（如果已请求）的情况下的远程对象值。</span><span class="sxs-lookup"><span data-stu-id="2a844-223">Remote object value in case of primitive values or JSON values (if it was requested).</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-224">unserializableValue</span><span class="sxs-lookup"><span data-stu-id="2a844-224">unserializableValue</span></span> <br/> <i><span data-ttu-id="2a844-225">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-225">optional</span></span></i></td>
            <td><a href="#unserializablevalue"><code class="flyout">UnserializableValue</code></a></td>
            <td><span data-ttu-id="2a844-226">不能为 JSON 的基元值-stringified 没有</span><span class="sxs-lookup"><span data-stu-id="2a844-226">Primitive value which can not be JSON-stringified does not have</span></span> <code>value</code><span data-ttu-id="2a844-227">，但获取此属性。</span><span class="sxs-lookup"><span data-stu-id="2a844-227">, but gets this property.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-228">description</span><span class="sxs-lookup"><span data-stu-id="2a844-228">description</span></span> <br/> <i><span data-ttu-id="2a844-229">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-229">optional</span></span></i></td>
            <td><code class="flyout">string</code></td>
            <td><span data-ttu-id="2a844-230">对象的字符串表示形式。</span><span class="sxs-lookup"><span data-stu-id="2a844-230">String representation of the object.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-231">objectId</span><span class="sxs-lookup"><span data-stu-id="2a844-231">objectId</span></span> <br/> <i><span data-ttu-id="2a844-232">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-232">optional</span></span></i></td>
            <td><a href="#remoteobjectid"><code class="flyout">RemoteObjectId</code></a></td>
            <td><span data-ttu-id="2a844-233">唯一对象标识符（对于非基元值）。</span><span class="sxs-lookup"><span data-stu-id="2a844-233">Unique object identifier (for non-primitive values).</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-234">msDebuggerPropertyId</span><span class="sxs-lookup"><span data-stu-id="2a844-234">msDebuggerPropertyId</span></span> <br/> <i><span data-ttu-id="2a844-235">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-235">optional</span></span></i></td>
            <td><code class="flyout">string</code></td>
            <td><span><b><span data-ttu-id="2a844-236">实验.</span><span class="sxs-lookup"><span data-stu-id="2a844-236">Experimental.</span></span> </b></span><span data-ttu-id="2a844-237">Microsoft：此对象的关联调试器属性 id。</span><span class="sxs-lookup"><span data-stu-id="2a844-237">Microsoft: The associated debugger property id for this object.</span></span></td>
        </tr>
    </tbody>
</table>

---

### <a name="propertydescriptor"></a> <span data-ttu-id="2a844-238">PropertyDescriptor</span><span class="sxs-lookup"><span data-stu-id="2a844-238">PropertyDescriptor</span></span> `object`

<span data-ttu-id="2a844-239">对象属性描述符。</span><span class="sxs-lookup"><span data-stu-id="2a844-239">Object property descriptor.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="2a844-240">属性</span><span class="sxs-lookup"><span data-stu-id="2a844-240">Properties</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="2a844-241">name</span><span class="sxs-lookup"><span data-stu-id="2a844-241">name</span></span></td>
            <td><code class="flyout">string</code></td>
            <td><span data-ttu-id="2a844-242">属性名称或符号描述。</span><span class="sxs-lookup"><span data-stu-id="2a844-242">Property name or symbol description.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-243">值</span><span class="sxs-lookup"><span data-stu-id="2a844-243">value</span></span> <br/> <i><span data-ttu-id="2a844-244">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-244">optional</span></span></i></td>
            <td><a href="#remoteobject"><code class="flyout">RemoteObject</code></a></td>
            <td><span data-ttu-id="2a844-245">与属性关联的值。</span><span class="sxs-lookup"><span data-stu-id="2a844-245">The value associated with the property.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-246">全</span><span class="sxs-lookup"><span data-stu-id="2a844-246">writable</span></span> <br/> <i><span data-ttu-id="2a844-247">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-247">optional</span></span></i></td>
            <td><code class="flyout">boolean</code></td>
            <td><span data-ttu-id="2a844-248">如果与属性关联的值可能更改（仅限数据描述符），则为 True。</span><span class="sxs-lookup"><span data-stu-id="2a844-248">True if the value associated with the property may be changed (data descriptors only).</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-249">获取</span><span class="sxs-lookup"><span data-stu-id="2a844-249">get</span></span> <br/> <i><span data-ttu-id="2a844-250">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-250">optional</span></span></i></td>
            <td><a href="#remoteobject"><code class="flyout">RemoteObject</code></a></td>
            <td><span data-ttu-id="2a844-251">充当属性的 getter 或没有 <code>undefined</code> getter （仅限访问器描述符）的函数。</span><span class="sxs-lookup"><span data-stu-id="2a844-251">A function which serves as a getter for the property, or <code>undefined</code> if there is no getter (accessor descriptors only).</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-252">set</span><span class="sxs-lookup"><span data-stu-id="2a844-252">set</span></span> <br/> <i><span data-ttu-id="2a844-253">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-253">optional</span></span></i></td>
            <td><a href="#remoteobject"><code class="flyout">RemoteObject</code></a></td>
            <td><span data-ttu-id="2a844-254">充当属性的 setter 的函数，或者没有 <code>undefined</code> setter （仅限访问器描述符）的函数。</span><span class="sxs-lookup"><span data-stu-id="2a844-254">A function which serves as a setter for the property, or <code>undefined</code> if there is no setter (accessor descriptors only).</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-255">旋钮</span><span class="sxs-lookup"><span data-stu-id="2a844-255">configurable</span></span></td>
            <td><code class="flyout">boolean</code></td>
            <td><span data-ttu-id="2a844-256">如果此属性描述符的类型可能已更改，并且该属性可能已从相应对象中删除，则为 True。</span><span class="sxs-lookup"><span data-stu-id="2a844-256">True if the type of this property descriptor may be changed and if the property may be deleted from the corresponding object.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-257">枚举</span><span class="sxs-lookup"><span data-stu-id="2a844-257">enumerable</span></span></td>
            <td><code class="flyout">boolean</code></td>
            <td><span data-ttu-id="2a844-258">如果在对相应对象的属性进行枚举时显示此属性，则为 True。</span><span class="sxs-lookup"><span data-stu-id="2a844-258">True if this property shows up during enumeration of the properties on the corresponding object.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-259">wasThrown</span><span class="sxs-lookup"><span data-stu-id="2a844-259">wasThrown</span></span> <br/> <i><span data-ttu-id="2a844-260">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-260">optional</span></span></i></td>
            <td><code class="flyout">boolean</code></td>
            <td><span data-ttu-id="2a844-261">如果计算期间引发了结果，则为 True。</span><span class="sxs-lookup"><span data-stu-id="2a844-261">True if the result was thrown during the evaluation.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-262">isOwn</span><span class="sxs-lookup"><span data-stu-id="2a844-262">isOwn</span></span> <br/> <i><span data-ttu-id="2a844-263">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-263">optional</span></span></i></td>
            <td><code class="flyout">boolean</code></td>
            <td><span data-ttu-id="2a844-264">如果属性为对象所拥有，则为 True。</span><span class="sxs-lookup"><span data-stu-id="2a844-264">True if the property is owned for the object.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-265">msReturnValue</span><span class="sxs-lookup"><span data-stu-id="2a844-265">msReturnValue</span></span> <br/> <i><span data-ttu-id="2a844-266">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-266">optional</span></span></i></td>
            <td><code class="flyout">boolean</code></td>
            <td><span><b><span data-ttu-id="2a844-267">实验.</span><span class="sxs-lookup"><span data-stu-id="2a844-267">Experimental.</span></span> </b></span><span data-ttu-id="2a844-268">Microsoft：如果属性为返回值，则为 True。</span><span class="sxs-lookup"><span data-stu-id="2a844-268">Microsoft: True if the property is a return value.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-269">符号</span><span class="sxs-lookup"><span data-stu-id="2a844-269">symbol</span></span> <br/> <i><span data-ttu-id="2a844-270">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-270">optional</span></span></i></td>
            <td><a href="#remoteobject"><code class="flyout">RemoteObject</code></a></td>
            <td><span data-ttu-id="2a844-271">属性符号对象（如果属性属于 `symbol` 类型）。</span><span class="sxs-lookup"><span data-stu-id="2a844-271">Property symbol object, if the property is of the `symbol` type.</span></span> </td>
        </tr>
    </tbody>
</table>

---

### <a name="callargument"></a> <span data-ttu-id="2a844-272">CallArgument</span><span class="sxs-lookup"><span data-stu-id="2a844-272">CallArgument</span></span> `object`

<span data-ttu-id="2a844-273">表示函数调用参数。</span><span class="sxs-lookup"><span data-stu-id="2a844-273">Represents function call argument.</span></span> <span data-ttu-id="2a844-274">远程对象 id <code>objectId</code> 、基元 <code>value</code> 、unserializable 基元值或两者均不是（对于未定义的）都应指定它们。</span><span class="sxs-lookup"><span data-stu-id="2a844-274">Either remote object id <code>objectId</code>, primitive <code>value</code>, unserializable primitive value or neither of (for undefined) them should be specified.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="2a844-275">属性</span><span class="sxs-lookup"><span data-stu-id="2a844-275">Properties</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="2a844-276">值</span><span class="sxs-lookup"><span data-stu-id="2a844-276">value</span></span> <br/> <i><span data-ttu-id="2a844-277">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-277">optional</span></span></i></td>
            <td><code class="flyout">any</code></td>
            <td><span data-ttu-id="2a844-278">基元值或可串行 javascript 对象。</span><span class="sxs-lookup"><span data-stu-id="2a844-278">Primitive value or serializable javascript object.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-279">unserializableValue</span><span class="sxs-lookup"><span data-stu-id="2a844-279">unserializableValue</span></span> <br/> <i><span data-ttu-id="2a844-280">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-280">optional</span></span></i></td>
            <td><a href="#unserializablevalue"><code class="flyout">UnserializableValue</code></a></td>
            <td><span data-ttu-id="2a844-281">不能为 JSON 的 stringified 的基元值。</span><span class="sxs-lookup"><span data-stu-id="2a844-281">Primitive value which can not be JSON-stringified.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-282">objectId</span><span class="sxs-lookup"><span data-stu-id="2a844-282">objectId</span></span> <br/> <i><span data-ttu-id="2a844-283">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-283">optional</span></span></i></td>
            <td><a href="#remoteobjectid"><code class="flyout">RemoteObjectId</code></a></td>
            <td><span data-ttu-id="2a844-284">远程对象句柄。</span><span class="sxs-lookup"><span data-stu-id="2a844-284">Remote object handle.</span></span></td>
        </tr>
    </tbody>
</table>

---

### <a name="executioncontextid"></a> <span data-ttu-id="2a844-285">ExecutionContextId</span><span class="sxs-lookup"><span data-stu-id="2a844-285">ExecutionContextId</span></span> `integer`

<span data-ttu-id="2a844-286">执行上下文的 Id。</span><span class="sxs-lookup"><span data-stu-id="2a844-286">Id of an execution context.</span></span>


---

### <a name="exceptiondetails"></a> <span data-ttu-id="2a844-287">ExceptionDetails</span><span class="sxs-lookup"><span data-stu-id="2a844-287">ExceptionDetails</span></span> `object`

<span data-ttu-id="2a844-288">有关在脚本编译或执行期间引发的异常（或错误）的详细信息。</span><span class="sxs-lookup"><span data-stu-id="2a844-288">Detailed information about exception (or error) that was thrown during script compilation or execution.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="2a844-289">属性</span><span class="sxs-lookup"><span data-stu-id="2a844-289">Properties</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="2a844-290">exceptionId</span><span class="sxs-lookup"><span data-stu-id="2a844-290">exceptionId</span></span></td>
            <td><code class="flyout">integer</code></td>
            <td><span data-ttu-id="2a844-291">异常 id。</span><span class="sxs-lookup"><span data-stu-id="2a844-291">Exception id.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-292">文本</span><span class="sxs-lookup"><span data-stu-id="2a844-292">text</span></span></td>
            <td><code class="flyout">string</code></td>
            <td><span data-ttu-id="2a844-293">异常文本，应与异常对象一起使用（如果可用）。</span><span class="sxs-lookup"><span data-stu-id="2a844-293">Exception text, which should be used together with exception object when available.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-294">lineNumber</span><span class="sxs-lookup"><span data-stu-id="2a844-294">lineNumber</span></span></td>
            <td><code class="flyout">integer</code></td>
            <td><span data-ttu-id="2a844-295">异常位置（从0开始）的行号。</span><span class="sxs-lookup"><span data-stu-id="2a844-295">Line number of the exception location (0-based).</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-296">columnNumber</span><span class="sxs-lookup"><span data-stu-id="2a844-296">columnNumber</span></span></td>
            <td><code class="flyout">integer</code></td>
            <td><span data-ttu-id="2a844-297">异常位置（从0开始）的列号。</span><span class="sxs-lookup"><span data-stu-id="2a844-297">Column number of the exception location (0-based).</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-298">scriptId</span><span class="sxs-lookup"><span data-stu-id="2a844-298">scriptId</span></span> <br/> <i><span data-ttu-id="2a844-299">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-299">optional</span></span></i></td>
            <td><a href="#scriptid"><code class="flyout">ScriptId</code></a></td>
            <td><span data-ttu-id="2a844-300">异常位置的脚本 ID。</span><span class="sxs-lookup"><span data-stu-id="2a844-300">Script ID of the exception location.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-301">url</span><span class="sxs-lookup"><span data-stu-id="2a844-301">url</span></span> <br/> <i><span data-ttu-id="2a844-302">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-302">optional</span></span></i></td>
            <td><code class="flyout">string</code></td>
            <td><span data-ttu-id="2a844-303">要在未报告脚本时使用的异常位置的 URL。</span><span class="sxs-lookup"><span data-stu-id="2a844-303">URL of the exception location, to be used when the script was not reported.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-304">stackTrace</span><span class="sxs-lookup"><span data-stu-id="2a844-304">stackTrace</span></span> <br/> <i><span data-ttu-id="2a844-305">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-305">optional</span></span></i></td>
            <td><a href="#stacktrace"><code class="flyout">StackTrace</code></a></td>
            <td><span data-ttu-id="2a844-306">JavaScript 堆栈跟踪（如果可用）。</span><span class="sxs-lookup"><span data-stu-id="2a844-306">JavaScript stack trace if available.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-307">除了</span><span class="sxs-lookup"><span data-stu-id="2a844-307">exception</span></span> <br/> <i><span data-ttu-id="2a844-308">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-308">optional</span></span></i></td>
            <td><a href="#remoteobject"><code class="flyout">RemoteObject</code></a></td>
            <td><span data-ttu-id="2a844-309">异常对象（如果可用）。</span><span class="sxs-lookup"><span data-stu-id="2a844-309">Exception object if available.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-310">executionContextId</span><span class="sxs-lookup"><span data-stu-id="2a844-310">executionContextId</span></span> <br/> <i><span data-ttu-id="2a844-311">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-311">optional</span></span></i></td>
            <td><a href="#executioncontextid"><code class="flyout">ExecutionContextId</code></a></td>
            <td><span data-ttu-id="2a844-312">发生异常的上下文的标识符。</span><span class="sxs-lookup"><span data-stu-id="2a844-312">Identifier of the context where exception happened.</span></span></td>
        </tr>
    </tbody>
</table>

---

### <a name="timestamp"></a> <span data-ttu-id="2a844-313">时间戳</span><span class="sxs-lookup"><span data-stu-id="2a844-313">Timestamp</span></span> `integer`

<span data-ttu-id="2a844-314">自 epoch 以来的毫秒数。</span><span class="sxs-lookup"><span data-stu-id="2a844-314">Number of milliseconds since epoch.</span></span>


---

### <a name="callframe"></a> <span data-ttu-id="2a844-315">CallFrame</span><span class="sxs-lookup"><span data-stu-id="2a844-315">CallFrame</span></span> `object`

<span data-ttu-id="2a844-316">运行时错误和断言的堆栈条目。</span><span class="sxs-lookup"><span data-stu-id="2a844-316">Stack entry for runtime errors and assertions.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="2a844-317">属性</span><span class="sxs-lookup"><span data-stu-id="2a844-317">Properties</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="2a844-318">functionName</span><span class="sxs-lookup"><span data-stu-id="2a844-318">functionName</span></span></td>
            <td><code class="flyout">string</code></td>
            <td><span data-ttu-id="2a844-319">JavaScript 函数名称。</span><span class="sxs-lookup"><span data-stu-id="2a844-319">JavaScript function name.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-320">scriptId</span><span class="sxs-lookup"><span data-stu-id="2a844-320">scriptId</span></span></td>
            <td><a href="#scriptid"><code class="flyout">ScriptId</code></a></td>
            <td><span data-ttu-id="2a844-321">JavaScript 脚本 id。</span><span class="sxs-lookup"><span data-stu-id="2a844-321">JavaScript script id.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-322">url</span><span class="sxs-lookup"><span data-stu-id="2a844-322">url</span></span></td>
            <td><code class="flyout">string</code></td>
            <td><span data-ttu-id="2a844-323">JavaScript 脚本名称或 url。</span><span class="sxs-lookup"><span data-stu-id="2a844-323">JavaScript script name or url.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-324">lineNumber</span><span class="sxs-lookup"><span data-stu-id="2a844-324">lineNumber</span></span></td>
            <td><code class="flyout">integer</code></td>
            <td><span data-ttu-id="2a844-325">JavaScript 脚本行数（基于0）。</span><span class="sxs-lookup"><span data-stu-id="2a844-325">JavaScript script line number (0-based).</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-326">columnNumber</span><span class="sxs-lookup"><span data-stu-id="2a844-326">columnNumber</span></span></td>
            <td><code class="flyout">integer</code></td>
            <td><span data-ttu-id="2a844-327">JavaScript 脚本列数（从0开始）。</span><span class="sxs-lookup"><span data-stu-id="2a844-327">JavaScript script column number (0-based).</span></span></td>
        </tr>
    </tbody>
</table>

---

### <a name="stacktrace"></a> <span data-ttu-id="2a844-328">StackTrace</span><span class="sxs-lookup"><span data-stu-id="2a844-328">StackTrace</span></span> `object`

<span data-ttu-id="2a844-329">调用断言或错误消息的帧。</span><span class="sxs-lookup"><span data-stu-id="2a844-329">Call frames for assertions or error messages.</span></span>

<table>
    <thead>
        <tr>
            <th><span data-ttu-id="2a844-330">属性</span><span class="sxs-lookup"><span data-stu-id="2a844-330">Properties</span></span></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><span data-ttu-id="2a844-331">description</span><span class="sxs-lookup"><span data-stu-id="2a844-331">description</span></span> <br/> <i><span data-ttu-id="2a844-332">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-332">optional</span></span></i></td>
            <td><code class="flyout">string</code></td>
            <td><span data-ttu-id="2a844-333">此堆栈跟踪的字符串标签。</span><span class="sxs-lookup"><span data-stu-id="2a844-333">String label of this stack trace.</span></span> <span data-ttu-id="2a844-334">对于异步跟踪，这可能是启动异步调用的函数的名称。</span><span class="sxs-lookup"><span data-stu-id="2a844-334">For async traces this may be a name of the function that initiated the async call.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-335">callFrames</span><span class="sxs-lookup"><span data-stu-id="2a844-335">callFrames</span></span></td>
            <td><a href="#callframe"><code class="flyout">CallFrame[]</code></a></td>
            <td><span data-ttu-id="2a844-336">JavaScript 函数名称。</span><span class="sxs-lookup"><span data-stu-id="2a844-336">JavaScript function name.</span></span></td>
        </tr>
        <tr>
            <td><span data-ttu-id="2a844-337">代</span><span class="sxs-lookup"><span data-stu-id="2a844-337">parent</span></span> <br/> <i><span data-ttu-id="2a844-338">可选</span><span class="sxs-lookup"><span data-stu-id="2a844-338">optional</span></span></i></td>
            <td><a href="#stacktrace"><code class="flyout">StackTrace</code></a></td>
            <td><span data-ttu-id="2a844-339">在此堆栈之前的异步 JavaScript 堆栈跟踪（如果可用）。</span><span class="sxs-lookup"><span data-stu-id="2a844-339">Asynchronous JavaScript stack trace that preceded this stack, if available.</span></span></td>
        </tr>
    </tbody>
</table>

---