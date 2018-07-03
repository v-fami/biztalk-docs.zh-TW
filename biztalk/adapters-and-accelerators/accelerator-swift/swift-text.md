---
title: SWIFT 文字 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SWIFT, text
ms.assetid: 90851d38-7789-4b1b-813b-7943f77ab984
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06e46c8be5da2f62f2b59ce2591e0559367adf08
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990927"
---
# <a name="swift-text"></a><span data-ttu-id="2a6a6-102">SWIFT 文字</span><span class="sxs-lookup"><span data-stu-id="2a6a6-102">SWIFT Text</span></span>
<span data-ttu-id="2a6a6-103">訊息文字的財務 (FIN) 訊息中，裝載所組成，並包含的所有資料欄位包含寄件者、 接收者和訊息型別欄位除外。</span><span class="sxs-lookup"><span data-stu-id="2a6a6-103">The message text makes up the payload of the financial (FIN) message, and contains all of the data fields except the fields containing the sender, receiver, and message type.</span></span> <span data-ttu-id="2a6a6-104">這三個欄位都包含在標頭部分。</span><span class="sxs-lookup"><span data-stu-id="2a6a6-104">These three fields are contained in the header portion.</span></span> <span data-ttu-id="2a6a6-105">有些訊息也包含選擇性使用者標頭，也會提供處理資訊。</span><span class="sxs-lookup"><span data-stu-id="2a6a6-105">Some messages also contain an optional User Header, which may also provide processing information.</span></span>  
  
 <span data-ttu-id="2a6a6-106">每個 FIN 訊息內容是由一系列已定義的序列中的欄位所組成。</span><span class="sxs-lookup"><span data-stu-id="2a6a6-106">Each FIN message payload consists of a series of fields in a defined sequence.</span></span> <span data-ttu-id="2a6a6-107">這些欄位會符合下列規則：</span><span class="sxs-lookup"><span data-stu-id="2a6a6-107">These fields conform to the following rules:</span></span>  
  
- <span data-ttu-id="2a6a6-108">欄位可能是必要或選擇性序列內。</span><span class="sxs-lookup"><span data-stu-id="2a6a6-108">The fields may be required or optional within the sequence.</span></span>  
  
- <span data-ttu-id="2a6a6-109">序列可能包含子序列，與子序列可能會在序列中重複。</span><span class="sxs-lookup"><span data-stu-id="2a6a6-109">A sequence may contain subsequences, and a subsequence may repeat within a sequence.</span></span>  
  
- <span data-ttu-id="2a6a6-110">您可以使用數種訊息類型中的欄位。</span><span class="sxs-lookup"><span data-stu-id="2a6a6-110">You can use a field in several message types.</span></span>  
  
- <span data-ttu-id="2a6a6-111">在欄位中可能有項目或子欄位。</span><span class="sxs-lookup"><span data-stu-id="2a6a6-111">Within a field, there may be elements or subfields.</span></span> <span data-ttu-id="2a6a6-112">項目或子欄位可能是通用於數個欄位。</span><span class="sxs-lookup"><span data-stu-id="2a6a6-112">An element or subfield may be common to several fields.</span></span>  
  
- <span data-ttu-id="2a6a6-113">每個重複的序列被以群組節點。</span><span class="sxs-lookup"><span data-stu-id="2a6a6-113">Each repeating sequence is represented by a group node.</span></span>  
  
- <span data-ttu-id="2a6a6-114">每個欄位可能本身有多個 nodal 層次，每個描述為一筆記錄。</span><span class="sxs-lookup"><span data-stu-id="2a6a6-114">Each field may itself have multiple nodal levels, each described as a record.</span></span>  
  
- <span data-ttu-id="2a6a6-115">結構描述項目代表只有最低的層級子欄位。</span><span class="sxs-lookup"><span data-stu-id="2a6a6-115">A schema element represents only the lowest level subfield.</span></span>  
  
- <span data-ttu-id="2a6a6-116">常見的記錄和項目中定義的一般和基底結構描述，如下所述。</span><span class="sxs-lookup"><span data-stu-id="2a6a6-116">Common records and elements are defined in the common and base schema, as described below.</span></span>  
  
- <span data-ttu-id="2a6a6-117">以數種格式 （例如合作對象的欄位），就可以表示的某些欄位。</span><span class="sxs-lookup"><span data-stu-id="2a6a6-117">Some fields may be represented in several formats (such as party fields).</span></span> <span data-ttu-id="2a6a6-118">這類欄位會定義為結構描述中的選項欄位。</span><span class="sxs-lookup"><span data-stu-id="2a6a6-118">Such fields are defined as choice fields in the schema.</span></span>  
  
  <span data-ttu-id="2a6a6-119">某些欄位具有有限的一組值。</span><span class="sxs-lookup"><span data-stu-id="2a6a6-119">Some fields have limited sets of values.</span></span> <span data-ttu-id="2a6a6-120">大部分的情況下，結構描述會列出這些值。</span><span class="sxs-lookup"><span data-stu-id="2a6a6-120">For the most part, the schema lists these values.</span></span> <span data-ttu-id="2a6a6-121">結構描述定義也包含字元集驗證。</span><span class="sxs-lookup"><span data-stu-id="2a6a6-121">Schema definitions also include character set validation.</span></span>