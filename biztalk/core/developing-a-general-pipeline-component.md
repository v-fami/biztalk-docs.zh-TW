---
title: 開發一般管線元件 |Microsoft Docs
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
ms.openlocfilehash: 8ca387b139a32606dea89f7c931c86245d151dcb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966687"
---
# <a name="developing-a-general-pipeline-component"></a><span data-ttu-id="8fd1d-102">開發一般管線元件</span><span class="sxs-lookup"><span data-stu-id="8fd1d-102">Developing a General Pipeline Component</span></span>

## <a name="interfaces"></a><span data-ttu-id="8fd1d-103">介面</span><span class="sxs-lookup"><span data-stu-id="8fd1d-103">Interfaces</span></span>
<span data-ttu-id="8fd1d-104">一般管線元件是實作下列介面的 .NET 或 COM 元件：</span><span class="sxs-lookup"><span data-stu-id="8fd1d-104">A general pipeline component is a .NET or COM component that implements the following interfaces:</span></span>  
  
- <span data-ttu-id="8fd1d-105">IBaseComponent 介面 (COM) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="8fd1d-105">IBaseComponent Interface (COM) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
  
- <span data-ttu-id="8fd1d-106">IComponent 介面 (COM) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="8fd1d-106">IComponent Interface (COM) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
  
- <span data-ttu-id="8fd1d-107">IComponentUI 介面 (COM) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="8fd1d-107">IComponentUI Interface (COM) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
  
- [<span data-ttu-id="8fd1d-108">IPersistPropertyBag</span><span class="sxs-lookup"><span data-stu-id="8fd1d-108">IPersistPropertyBag</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.ipersistpropertybag)
  
  <span data-ttu-id="8fd1d-109">一般管線元件會從 BizTalk「傳訊引擎」取得一個訊息、處理該訊息，接著將它傳回 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 引擎。</span><span class="sxs-lookup"><span data-stu-id="8fd1d-109">A general pipeline component gets one message from the BizTalk Messaging Engine, processes it, and returns it to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] engine.</span></span> <span data-ttu-id="8fd1d-110">一般元件也可以經過實作，使其不將訊息傳回至伺服器。</span><span class="sxs-lookup"><span data-stu-id="8fd1d-110">General components can also be implemented so that they do not return messages to the server.</span></span> <span data-ttu-id="8fd1d-111">這種元件稱為耗用元件，因為元件會接收訊息但不會產生任何結果訊息。</span><span class="sxs-lookup"><span data-stu-id="8fd1d-111">Such components are called consuming components because the component receives messages but does not produce any result messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8fd1d-112">自訂管線元件應將任何額外的部分從輸入訊息複製到輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="8fd1d-112">Custom pipeline components should copy any additional parts from the input message to the output message(s).</span></span> <span data-ttu-id="8fd1d-113">其用意是要將這些部分保留到管線中做進一步處理。</span><span class="sxs-lookup"><span data-stu-id="8fd1d-113">This preserves them for further processing in the pipeline.</span></span>  
  
## <a name="more-pipeline-resources"></a><span data-ttu-id="8fd1d-114">更多管線資源</span><span class="sxs-lookup"><span data-stu-id="8fd1d-114">More pipeline resources</span></span>
 <span data-ttu-id="8fd1d-115">[開發組合管線元件](../core/developing-an-assembling-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="8fd1d-115">[Developing an Assembling Pipeline Component](../core/developing-an-assembling-pipeline-component.md) </span></span>  
 <span data-ttu-id="8fd1d-116">[開發解譯管線元件](../core/developing-a-disassembling-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="8fd1d-116">[Developing a Disassembling Pipeline Component](../core/developing-a-disassembling-pipeline-component.md) </span></span>  
 <span data-ttu-id="8fd1d-117">[開發探查管線元件](../core/developing-a-probing-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="8fd1d-117">[Developing a Probing Pipeline Component](../core/developing-a-probing-pipeline-component.md) </span></span>  
 <span data-ttu-id="8fd1d-118">[報告管線元件錯誤](../core/reporting-errors-from-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="8fd1d-118">[Reporting Errors from Pipeline Components](../core/reporting-errors-from-pipeline-components.md) </span></span>  
 <span data-ttu-id="8fd1d-119">[設定原生管線元件](../core/configuring-native-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="8fd1d-119">[Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md) </span></span>  
 <span data-ttu-id="8fd1d-120">[部署管線元件](../core/deploying-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="8fd1d-120">[Deploying Pipeline Components](../core/deploying-pipeline-components.md) </span></span>  
 [<span data-ttu-id="8fd1d-121">CustomComponent (BizTalk Server 範例)</span><span class="sxs-lookup"><span data-stu-id="8fd1d-121">CustomComponent (BizTalk Server Sample)</span></span>](../core/customcomponent-biztalk-server-sample.md)