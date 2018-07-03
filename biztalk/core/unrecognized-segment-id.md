---
title: 無法辨識的區段識別碼 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a00fe451-0a84-4dca-980c-682243fc9804
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2a3990ce9a1d913cdb9840605c6f0e34623db8b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007537"
---
# <a name="unrecognized-segment-id"></a><span data-ttu-id="dd77e-102">無法辨識的區段識別碼</span><span class="sxs-lookup"><span data-stu-id="dd77e-102">Unrecognized segment ID</span></span>
## <a name="details"></a><span data-ttu-id="dd77e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="dd77e-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="dd77e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="dd77e-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="dd77e-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="dd77e-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="dd77e-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="dd77e-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="dd77e-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="dd77e-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="dd77e-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="dd77e-108"> EDI</span></span> |
|    <span data-ttu-id="dd77e-109">元件</span><span class="sxs-lookup"><span data-stu-id="dd77e-109">Component</span></span>    |                                       <span data-ttu-id="dd77e-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="dd77e-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="dd77e-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="dd77e-111">Symbolic Name</span></span>  | <span data-ttu-id="dd77e-112">EfactUnrecognizedSegmentIDDescription</span><span class="sxs-lookup"><span data-stu-id="dd77e-112">EfactUnrecognizedSegmentIDDescription</span></span><br /><br /> <span data-ttu-id="dd77e-113">X12UnrecognizedSegmentIDDescription</span><span class="sxs-lookup"><span data-stu-id="dd77e-113">X12UnrecognizedSegmentIDDescription</span></span>  |
|  <span data-ttu-id="dd77e-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="dd77e-114">Message Text</span></span>   |                                <span data-ttu-id="dd77e-115">無法辨識的區段識別碼</span><span class="sxs-lookup"><span data-stu-id="dd77e-115">Unrecognized segment ID</span></span>                                 |
  
## <a name="explanation"></a><span data-ttu-id="dd77e-116">說明</span><span class="sxs-lookup"><span data-stu-id="dd77e-116">Explanation</span></span>  
 <span data-ttu-id="dd77e-117">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為對應的文件結構描述未定義在交換中交易集的區段。</span><span class="sxs-lookup"><span data-stu-id="dd77e-117">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because a segment in a transaction set in the interchange was not defined by the corresponding document schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dd77e-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="dd77e-118">User Action</span></span>  
 <span data-ttu-id="dd77e-119">若要解決這個錯誤，將傳送者的交換移除無法辨識的區段，並重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="dd77e-119">To resolve this error, have the sender of the interchange remove the unrecognized segment and resend the interchange.</span></span>