---
title: 處理內送資料流管線元件中的 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a1b7c4f7-99ba-4bfa-89ab-1fabfe0845d1
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20fc34da3a5c8e65f81cd6bbbb699f52506cdc6b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246566"
---
# <a name="handling-incoming-data-streams-in-pipeline-components"></a><span data-ttu-id="c6267-102">處理管線元件中的內送資料流</span><span class="sxs-lookup"><span data-stu-id="c6267-102">Handling Incoming Data Streams in Pipeline Components</span></span>
<span data-ttu-id="c6267-103">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中撰寫管線元件的自訂解譯器程式碼時，應考量下列事項：</span><span class="sxs-lookup"><span data-stu-id="c6267-103">The following considerations should be made when writing custom disassembler code for pipeline components in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="do-not-close-the-incoming-data-stream-in-custom-dissasember-code"></a><span data-ttu-id="c6267-104">請勿關閉自訂解譯器程式碼中的內送資料流</span><span class="sxs-lookup"><span data-stu-id="c6267-104">Do not close the incoming data stream in custom dissasember code</span></span>  
 <span data-ttu-id="c6267-105">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中撰寫管線元件的自訂解譯器程式碼時，請確定您未關閉解譯器程式碼中的內送資料流。</span><span class="sxs-lookup"><span data-stu-id="c6267-105">When you write custom disassembler code for pipeline components in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ensure that you do not close the incoming data stream in the disassembler code.</span></span> <span data-ttu-id="c6267-106">來自輸入訊息的內送資料流是共用的資源。</span><span class="sxs-lookup"><span data-stu-id="c6267-106">The incoming stream from the input message is a shared resource.</span></span> <span data-ttu-id="c6267-107">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 訊息引擎中的訊息內容追蹤元件也會使用內送資料流。</span><span class="sxs-lookup"><span data-stu-id="c6267-107">The incoming stream is also used by the message body tracking component in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] message engine.</span></span>  
  
 <span data-ttu-id="c6267-108">如果您以隱含或明確關閉的內送資料流，追蹤資料可能會遺失，您將無法檢查使用訊息事件和服務執行個體追蹤中的資料流資料[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c6267-108">If you either implicitly or explicitly close the incoming stream, tracking data may be lost and you will be unable to examine the stream data using message event and service instance tracking in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="use-the-seek-method-of-the-stream-class-to-set-the-data-stream-pointer-to-the-start-of-the-stream"></a><span data-ttu-id="c6267-109">使用 Stream 類別的 Seek 方法將資料流指標設定到資料流的開頭</span><span class="sxs-lookup"><span data-stu-id="c6267-109">Use the Seek method of the Stream class to set the data stream pointer to the start of the stream</span></span>  
 <span data-ttu-id="c6267-110">請確定您讀取了完整的內送資料流，直到讀完資料流結尾為止。</span><span class="sxs-lookup"><span data-stu-id="c6267-110">Ensure that you read from the incoming data stream until the end of the stream is reached.</span></span> <span data-ttu-id="c6267-111">例如，如果自訂程式碼要求讀取 300 KB 的資料，而程式碼只收到 34 KB 的資料時，請勿假設已到達資料流的結尾。</span><span class="sxs-lookup"><span data-stu-id="c6267-111">For example, if custom code makes a read request for 300 KB of data and the code only receives 34 KB of data, do not assume that the end of the stream has been reached.</span></span> <span data-ttu-id="c6267-112">自訂程式碼應該一律從內送資料流讀取，直到傳回 0 個位元組為止。</span><span class="sxs-lookup"><span data-stu-id="c6267-112">The custom code should always read from the incoming stream until 0 bytes is returned.</span></span>  
  
 <span data-ttu-id="c6267-113">在自訂元件邏輯中傳回資料流之前，請先將資料流指標設回資料流的開頭。</span><span class="sxs-lookup"><span data-stu-id="c6267-113">Before returning the data stream in the custom component logic, set the data stream pointer back to the start of the stream.</span></span> <span data-ttu-id="c6267-114">例如，此程式碼示範使用 Seek 方法，在傳回資料流之前指向資料流開頭的邏輯：</span><span class="sxs-lookup"><span data-stu-id="c6267-114">For example, this code illustrates logic to use the seek method to point to the beginning of the stream before returning the stream:</span></span>  
  
```  
myDataStream.Seek(0, SeekOrigin.Begin);  
return myDataStream;  
```  
  
 <span data-ttu-id="c6267-115">如果您未執行上述動作，且資料流讀取到目前元件中的結尾，下一個元件就會收到顯示為空的資料流，因為資料流指標未設定到資料流的開頭。</span><span class="sxs-lookup"><span data-stu-id="c6267-115">If you do not do this and the stream is read to the end in the current component, the next component receives what appears to be an empty stream because the data stream pointer was not set to the start of the stream.</span></span> <span data-ttu-id="c6267-116">這可能會在後續的管線元件中造成未預期的剖析和驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="c6267-116">This can cause unexpected parsing and validation errors in subsequent pipeline components.</span></span>