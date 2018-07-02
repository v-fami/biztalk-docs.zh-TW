---
title: 無法在 AS2 EDIINT MIC 表格中建立項目 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a1c75d70-e39e-4465-b32b-db646c059c9b
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d0a9cf5f472a449d8632553ec41738c7e4ebd9f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970447"
---
# <a name="unable-to-create-the-entry-in-the-as2-ediint-mic-table"></a><span data-ttu-id="f40d5-102">無法在 AS2 EDIINT MIC 表格中建立項目</span><span class="sxs-lookup"><span data-stu-id="f40d5-102">Unable to create the entry in the AS2 EDIINT MIC table</span></span>
## <a name="details"></a><span data-ttu-id="f40d5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f40d5-103">Details</span></span>  
  
|                 |                                                                                                                                                                               |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="f40d5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f40d5-104">Product Name</span></span>   |                                              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                               |
| <span data-ttu-id="f40d5-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="f40d5-105">Product Version</span></span> |                                                          [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                           |
|    <span data-ttu-id="f40d5-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f40d5-106">Event ID</span></span>     |                                                                                       -                                                                                       |
|  <span data-ttu-id="f40d5-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="f40d5-107">Event Source</span></span>   |                                            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f40d5-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="f40d5-108"> EDI</span></span>                                             |
|    <span data-ttu-id="f40d5-109">元件</span><span class="sxs-lookup"><span data-stu-id="f40d5-109">Component</span></span>    |                                                                                  <span data-ttu-id="f40d5-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="f40d5-110">AS2 Engine</span></span>                                                                                   |
|  <span data-ttu-id="f40d5-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f40d5-111">Symbolic Name</span></span>  |                                                                        <span data-ttu-id="f40d5-112">AS2MicDataStoreCreateEntryError</span><span class="sxs-lookup"><span data-stu-id="f40d5-112">AS2MicDataStoreCreateEntryError</span></span>                                                                        |
|  <span data-ttu-id="f40d5-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f40d5-113">Message Text</span></span>   | <span data-ttu-id="f40d5-114">無法在 AS2 EDIINT MIC 表格中建立項目。</span><span class="sxs-lookup"><span data-stu-id="f40d5-114">Unable to create the entry in the AS2 EDIINT MIC table.</span></span> <span data-ttu-id="f40d5-115">這可能因重複的 AS2-From、as2-以和 MessageID 組合寫入至資料表。</span><span class="sxs-lookup"><span data-stu-id="f40d5-115">This could be caused by duplicate AS2-From, AS2-To and MessageID combinations being written to the table.</span></span>  <span data-ttu-id="f40d5-116">錯誤： {0}</span><span class="sxs-lookup"><span data-stu-id="f40d5-116">Error: {0}</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="f40d5-117">說明</span><span class="sxs-lookup"><span data-stu-id="f40d5-117">Explanation</span></span>  
 <span data-ttu-id="f40d5-118">此錯誤表示資料庫連接問題或資料庫資料表中存在索引鍵的資料列。</span><span class="sxs-lookup"><span data-stu-id="f40d5-118">This error indicates either database connection problems or the row keys already exist in the database table.</span></span> <span data-ttu-id="f40d5-119">完整的錯誤訊息應該提供插入作業的失敗原因的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f40d5-119">The full error message should provide information as to why the insert operation failed.</span></span> <span data-ttu-id="f40d5-120">MDN 收到之後 （不論成功或失敗），以便在收到 MDN 之後，應該永遠不會發生此錯誤，則會移除資料表中的項目。</span><span class="sxs-lookup"><span data-stu-id="f40d5-120">The entries in the table are removed after the MDN has been received (whether successful or failed), so this error should never happen after the MDN has been received.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f40d5-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f40d5-121">User Action</span></span>  
 <span data-ttu-id="f40d5-122">若要解決這個錯誤，請檢查完整的錯誤訊息，如需插入作業失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="f40d5-122">To resolve this error, check the full error message for information about why the insert operation failed.</span></span> <span data-ttu-id="f40d5-123">在 SQL 中，在 EDIINT_MIC 資料表中，判斷是否有重複的 AS2-從和 AS2-MessageID 來組合。</span><span class="sxs-lookup"><span data-stu-id="f40d5-123">In SQL, in the EDIINT_MIC table, determine whether there is duplicate AS2-From and AS2-To MessageID combinations.</span></span> <span data-ttu-id="f40d5-124">如果是的話，請將它們移除。</span><span class="sxs-lookup"><span data-stu-id="f40d5-124">If so, remove them.</span></span>