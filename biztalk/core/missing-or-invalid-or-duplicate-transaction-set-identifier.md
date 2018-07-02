---
title: 遺失、 無效或重複的交易集識別項 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8580aab2-9fa4-43fb-b643-10621926591e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 476b510396d29d5f4e85a13ed7c3bca3ee3fcef3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971719"
---
# <a name="missing-or-invalid-or-duplicate-transaction-set-identifier"></a><span data-ttu-id="50c36-102">遺失、 無效或重複的交易集識別項</span><span class="sxs-lookup"><span data-stu-id="50c36-102">Missing or invalid or duplicate Transaction set identifier</span></span>
## <a name="details"></a><span data-ttu-id="50c36-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="50c36-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="50c36-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="50c36-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="50c36-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="50c36-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="50c36-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="50c36-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="50c36-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="50c36-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="50c36-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="50c36-108"> EDI</span></span> |
|    <span data-ttu-id="50c36-109">元件</span><span class="sxs-lookup"><span data-stu-id="50c36-109">Component</span></span>    |                                       <span data-ttu-id="50c36-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="50c36-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="50c36-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="50c36-111">Symbolic Name</span></span>  |                      <span data-ttu-id="50c36-112">X12TsMissingOrInvalidTsIdentiferDescription2</span><span class="sxs-lookup"><span data-stu-id="50c36-112">X12TsMissingOrInvalidTsIdentiferDescription2</span></span>                      |
|  <span data-ttu-id="50c36-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="50c36-113">Message Text</span></span>   |            <span data-ttu-id="50c36-114">遺失、 無效或重複的交易集識別項 '{0}'</span><span class="sxs-lookup"><span data-stu-id="50c36-114">Missing or invalid or duplicate Transaction set identifier '{0}'</span></span>            |
  
## <a name="explanation"></a><span data-ttu-id="50c36-115">說明</span><span class="sxs-lookup"><span data-stu-id="50c36-115">Explanation</span></span>  
 <span data-ttu-id="50c36-116">這個錯誤/警告/資訊事件表示接收或傳送管線無法處理 X12 交換設定值，交易識別碼 （ST01 欄位中），因為已遺失、 重複項目，或具有無效的值。</span><span class="sxs-lookup"><span data-stu-id="50c36-116">This Error/Warning/Information event indicates that the receive or send pipeline could not process the X12 interchange because the value of the transaction set identifier (in the ST01 field) was missing, a duplicate, or had an invalid value.</span></span> <span data-ttu-id="50c36-117">如果文件結構描述沒有 ST 標頭和 SE 結尾，也可能會發生。</span><span class="sxs-lookup"><span data-stu-id="50c36-117">This can occur if the document schema does not have an ST header and an SE trailer.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="50c36-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="50c36-118">User Action</span></span>  
 <span data-ttu-id="50c36-119">若要解決這個錯誤，請確定交換具有 ST01 欄位的值，而且結構描述具有 ST 標頭和 SE 結尾的項目。</span><span class="sxs-lookup"><span data-stu-id="50c36-119">To resolve this error, make sure that the interchange has a value for the ST01 field and that the schema has an entry for the ST header and SE trailer.</span></span> <span data-ttu-id="50c36-120">確認的 ST01 值是有效的三位數的文件類型指示項。</span><span class="sxs-lookup"><span data-stu-id="50c36-120">Verify that the value of ST01 is a valid three-digit document-type designator.</span></span> <span data-ttu-id="50c36-121">確認 ST01 欄位不是與另一個交易集合的 ST01 欄位重複。</span><span class="sxs-lookup"><span data-stu-id="50c36-121">Verify that the ST01 field is not a duplicate with the ST01 field of another transaction set.</span></span>