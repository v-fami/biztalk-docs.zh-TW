---
title: 開發一般管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 63f5d8d1-30fb-4a1e-b4bd-2be07b618b20
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44b85992eb0691b7f27ec1a52812d986429d9e31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239214"
---
# <a name="developing-a-general-pipeline-component"></a><span data-ttu-id="c4b0f-102">開發一般管線元件</span><span class="sxs-lookup"><span data-stu-id="c4b0f-102">Developing a General Pipeline Component</span></span>

## <a name="interfaces"></a><span data-ttu-id="c4b0f-103">介面</span><span class="sxs-lookup"><span data-stu-id="c4b0f-103">Interfaces</span></span>
<span data-ttu-id="c4b0f-104">一般管線元件是實作下列介面的 .NET 或 COM 元件：</span><span class="sxs-lookup"><span data-stu-id="c4b0f-104">A general pipeline component is a .NET or COM component that implements the following interfaces:</span></span>  
  
-   <span data-ttu-id="c4b0f-105">IBaseComponent 介面 (COM)[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="c4b0f-105">IBaseComponent Interface (COM) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
  
-   <span data-ttu-id="c4b0f-106">IComponent 介面 (COM)[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="c4b0f-106">IComponent Interface (COM) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
  
-   <span data-ttu-id="c4b0f-107">IComponentUI 介面 (COM)[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="c4b0f-107">IComponentUI Interface (COM) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
  
-   [<span data-ttu-id="c4b0f-108">IPersistPropertyBag</span><span class="sxs-lookup"><span data-stu-id="c4b0f-108">IPersistPropertyBag</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.ipersistpropertybag)
  
 <span data-ttu-id="c4b0f-109">一般管線元件會從 BizTalk「傳訊引擎」取得一個訊息、處理該訊息，接著將它傳回 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 引擎。</span><span class="sxs-lookup"><span data-stu-id="c4b0f-109">A general pipeline component gets one message from the BizTalk Messaging Engine, processes it, and returns it to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] engine.</span></span> <span data-ttu-id="c4b0f-110">一般元件也可以經過實作，使其不將訊息傳回至伺服器。</span><span class="sxs-lookup"><span data-stu-id="c4b0f-110">General components can also be implemented so that they do not return messages to the server.</span></span> <span data-ttu-id="c4b0f-111">這種元件稱為耗用元件，因為元件會接收訊息但不會產生任何結果訊息。</span><span class="sxs-lookup"><span data-stu-id="c4b0f-111">Such components are called consuming components because the component receives messages but does not produce any result messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4b0f-112">自訂管線元件應將任何額外的部分從輸入訊息複製到輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="c4b0f-112">Custom pipeline components should copy any additional parts from the input message to the output message(s).</span></span> <span data-ttu-id="c4b0f-113">其用意是要將這些部分保留到管線中做進一步處理。</span><span class="sxs-lookup"><span data-stu-id="c4b0f-113">This preserves them for further processing in the pipeline.</span></span>  
  
## <a name="more-pipeline-resources"></a><span data-ttu-id="c4b0f-114">更多的管線資源</span><span class="sxs-lookup"><span data-stu-id="c4b0f-114">More pipeline resources</span></span>
 <span data-ttu-id="c4b0f-115">[開發組合管線元件](../core/developing-an-assembling-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="c4b0f-115">[Developing an Assembling Pipeline Component](../core/developing-an-assembling-pipeline-component.md) </span></span>  
 <span data-ttu-id="c4b0f-116">[開發解譯管線元件](../core/developing-a-disassembling-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="c4b0f-116">[Developing a Disassembling Pipeline Component](../core/developing-a-disassembling-pipeline-component.md) </span></span>  
 <span data-ttu-id="c4b0f-117">[開發探查管線元件](../core/developing-a-probing-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="c4b0f-117">[Developing a Probing Pipeline Component](../core/developing-a-probing-pipeline-component.md) </span></span>  
 <span data-ttu-id="c4b0f-118">[報告管線元件錯誤](../core/reporting-errors-from-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="c4b0f-118">[Reporting Errors from Pipeline Components](../core/reporting-errors-from-pipeline-components.md) </span></span>  
 <span data-ttu-id="c4b0f-119">[設定原生管線元件](../core/configuring-native-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="c4b0f-119">[Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md) </span></span>  
 <span data-ttu-id="c4b0f-120">[部署管線元件](../core/deploying-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="c4b0f-120">[Deploying Pipeline Components](../core/deploying-pipeline-components.md) </span></span>  
 [<span data-ttu-id="c4b0f-121">CustomComponent （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="c4b0f-121">CustomComponent (BizTalk Server Sample)</span></span>](../core/customcomponent-biztalk-server-sample.md)