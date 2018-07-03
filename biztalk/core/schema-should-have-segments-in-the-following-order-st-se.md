---
title: 結構描述區段應該依照下列順序 ST...SE |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f4d1c6a-7d48-413a-9ef5-a0c49773dc16
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c98bc756e4bd75a8a15111c54f433a7f9c6c0509
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015167"
---
# <a name="schema-should-have-segments-in-the-following-order-st--se"></a><span data-ttu-id="789cb-102">結構描述區段應該依照下列順序 ST...SE</span><span class="sxs-lookup"><span data-stu-id="789cb-102">Schema should have segments in the following order ST .... SE</span></span>
## <a name="details"></a><span data-ttu-id="789cb-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="789cb-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="789cb-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="789cb-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="789cb-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="789cb-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="789cb-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="789cb-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="789cb-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="789cb-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="789cb-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="789cb-108"> EDI</span></span> |
|    <span data-ttu-id="789cb-109">元件</span><span class="sxs-lookup"><span data-stu-id="789cb-109">Component</span></span>    |                                       <span data-ttu-id="789cb-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="789cb-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="789cb-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="789cb-111">Symbolic Name</span></span>  |                    <span data-ttu-id="789cb-112">SchemaCode116ETransactionSetSchemaStSeOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="789cb-112">SchemaCode116ETransactionSetSchemaStSeOutOfOrder</span></span>                    |
|  <span data-ttu-id="789cb-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="789cb-113">Message Text</span></span>   |             <span data-ttu-id="789cb-114">結構描述區段應該依照下列順序 ST...SE</span><span class="sxs-lookup"><span data-stu-id="789cb-114">Schema should have segments in the following order ST .... SE</span></span>              |
  
## <a name="explanation"></a><span data-ttu-id="789cb-115">說明</span><span class="sxs-lookup"><span data-stu-id="789cb-115">Explanation</span></span>  
 <span data-ttu-id="789cb-116">這個錯誤/警告/資訊事件表示自訂文件結構描述不正確的因為標頭和結尾不是處於正確的順序。</span><span class="sxs-lookup"><span data-stu-id="789cb-116">This Error/Warning/Information event indicates that a custom document schema is invalid because the headers and trailers were not in the correct order.</span></span> <span data-ttu-id="789cb-117">部署結構描述時，BizTalk Server 會執行這項驗證。</span><span class="sxs-lookup"><span data-stu-id="789cb-117">BizTalk Server performs this validation when the schema is deployed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="789cb-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="789cb-118">User Action</span></span>  
 <span data-ttu-id="789cb-119">若要解決這個錯誤，請變更自訂文件結構描述，以便標頭和結尾會以正確的順序，並重新部署結構描述。</span><span class="sxs-lookup"><span data-stu-id="789cb-119">To resolve this error, change the customized document schema so that the headers and trailers are in the correct order, and then redeploy the schema.</span></span>