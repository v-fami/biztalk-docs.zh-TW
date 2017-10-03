---
title: "報告管線元件錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IErrorInfo object
- pipeline components [custom], errors
- SetErrorInfo method
- Exception object
ms.assetid: ad7c519e-829a-4a92-a42f-3e367d5dbaa8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d181f557d64152ff79f70b09986c05727076121
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="reporting-errors-from-pipeline-components"></a><span data-ttu-id="2bf2a-102">報告管線元件錯誤</span><span class="sxs-lookup"><span data-stu-id="2bf2a-102">Reporting Errors from Pipeline Components</span></span>
<span data-ttu-id="2bf2a-103">管線元件會使用兩種方法來報告錯誤：</span><span class="sxs-lookup"><span data-stu-id="2bf2a-103">Pipeline components report errors in two ways:</span></span>  
  
-   <span data-ttu-id="2bf2a-104">如果是 .NET 元件，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2bf2a-104">For .NET-based components, by throwing an exception.</span></span>  
  
-   <span data-ttu-id="2bf2a-105">以 COM 為基礎的元件，藉由設定**ErrorInfo**物件並傳回失敗 HRESULT 而失敗。</span><span class="sxs-lookup"><span data-stu-id="2bf2a-105">For COM-based components, by setting the **ErrorInfo** object and returning a failure HRESULT.</span></span>  
  
## <a name="reporting-errors-from-net-pipeline-components"></a><span data-ttu-id="2bf2a-106">報告 .NET 管線元件錯誤</span><span class="sxs-lookup"><span data-stu-id="2bf2a-106">Reporting errors from .NET pipeline components</span></span>  
 <span data-ttu-id="2bf2a-107">若要報告錯誤，.NET 管線元件需要擲回例外狀況，以報告此錯誤的描述。</span><span class="sxs-lookup"><span data-stu-id="2bf2a-107">To report an error, a .NET-based pipeline component needs to throw an exception where it reports the error description.</span></span> <span data-ttu-id="2bf2a-108">若要報告擲回錯誤之元件的名稱，請設定**來源**屬性**例外狀況**物件。</span><span class="sxs-lookup"><span data-stu-id="2bf2a-108">To report the name of the component that throws an error, set the **Source** property of the **Exception** object.</span></span>  
  
 <span data-ttu-id="2bf2a-109">「 傳訊引擎會使用**訊息**和**來源**屬性**例外狀況**来報告錯誤的物件。</span><span class="sxs-lookup"><span data-stu-id="2bf2a-109">The Messaging Engine uses the **Message** and **Source** properties of the **Exception** object to report an error.</span></span> <span data-ttu-id="2bf2a-110">下列訊息會寫入事件記錄：</span><span class="sxs-lookup"><span data-stu-id="2bf2a-110">The following message is written to the event log:</span></span>  
  
 <span data-ttu-id="2bf2a-111">「 失敗執行 [接收 &#124; 傳送] 管線：\<管線名稱 > 來源：\<來源 > [接收位置 &#124;傳送埠:]\<位置 &#124; 連接埠名稱 > 原因：\<訊息 >。 」</span><span class="sxs-lookup"><span data-stu-id="2bf2a-111">"There was a failure executing the [receive&#124;send] pipeline: \<pipeline name> Source: \<Source> [Receive Location&#124;Send Port:] \<location&#124;port name> Reason: \<Message>."</span></span>  
  
## <a name="reporting-errors-from-com-pipeline-components"></a><span data-ttu-id="2bf2a-112">報告 COM 管線元件錯誤</span><span class="sxs-lookup"><span data-stu-id="2bf2a-112">Reporting errors from COM pipeline components</span></span>  
 <span data-ttu-id="2bf2a-113">為了報告錯誤，COM 管線元件會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="2bf2a-113">To report an error, COM-based pipeline components perform the following actions:</span></span>  
  
1.  <span data-ttu-id="2bf2a-114">管線元件集**IErrorInfo**藉由呼叫物件**SetErrorInfo**方法。</span><span class="sxs-lookup"><span data-stu-id="2bf2a-114">The pipeline component sets the **IErrorInfo** object by calling the **SetErrorInfo** method.</span></span>  
  
2.  <span data-ttu-id="2bf2a-115">管線元件會將失敗的 HRESULT 傳給傳訊引擎。</span><span class="sxs-lookup"><span data-stu-id="2bf2a-115">The pipeline component returns a failed HRESULT to the Messaging Engine.</span></span>  
  
 <span data-ttu-id="2bf2a-116">「 傳訊引擎會使用**Ierrorinfo**和**GetDescription**屬性**IErrorInfo**来報告錯誤的物件。</span><span class="sxs-lookup"><span data-stu-id="2bf2a-116">The Messaging Engine uses the **GetSource** and **GetDescription** properties of the **IErrorInfo** object to report an error.</span></span> <span data-ttu-id="2bf2a-117">如果未設定來源，則會使用此元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="2bf2a-117">If the source is not set, the name of the component is used.</span></span> <span data-ttu-id="2bf2a-118">如果描述不是集合或整個**ErrorInfo**未設定物件，傳回的 HRESULT 會報告而不是描述。</span><span class="sxs-lookup"><span data-stu-id="2bf2a-118">If the description is not set or the whole **ErrorInfo** object is not set, the returned HRESULT is reported instead of the description.</span></span> <span data-ttu-id="2bf2a-119">下列訊息會寫入事件記錄：</span><span class="sxs-lookup"><span data-stu-id="2bf2a-119">The following message is written to the event log:</span></span>  
  
 <span data-ttu-id="2bf2a-120">「 失敗執行 [接收 &#124; 傳送] 管線：\<管線名稱 > 來源： \<Ierrorinfo > [接收位置 &#124;傳送埠:]\<位置 &#124; 連接埠名稱 > 原因： \<GetDescription 或 HRESULT >。 」</span><span class="sxs-lookup"><span data-stu-id="2bf2a-120">"There was a failure executing the [receive&#124;send] pipeline: \<pipeline name> Source: \<GetSource> [Receive Location&#124;Send Port:] \<location&#124;port name> Reason: \<GetDescription or HRESULT>."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bf2a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2bf2a-121">See Also</span></span>  
 [<span data-ttu-id="2bf2a-122">開發自訂管線元件</span><span class="sxs-lookup"><span data-stu-id="2bf2a-122">Developing Custom Pipeline Components</span></span>](../core/developing-custom-pipeline-components.md)