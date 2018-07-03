---
title: 從舊版 BizTalk Server 移轉結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bdc86401-2002-40b8-a919-2c00cf42b557
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54b9dba1ee759cd33f7f3db44553684c27b57d10
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022460"
---
# <a name="schema-migration-from-previous-versions-of-biztalk-server"></a><span data-ttu-id="d2742-102">從舊版 BizTalk Server 移轉結構描述</span><span class="sxs-lookup"><span data-stu-id="d2742-102">Schema Migration from Previous Versions of BizTalk Server</span></span>
<span data-ttu-id="d2742-103">此版本的 BizTalk Server 使用「XML 結構描述定義」(XSD) 語言來表示訊息結構描述，舊版則使用 XML-Data Reduced (XDR) 語法來表示訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="d2742-103">This version of BizTalk Server uses XML Schema definition (XSD) language to represent message schemas, while previous versions used the XML-Data Reduced (XDR) syntax to represent message schemas.</span></span> <span data-ttu-id="d2742-104">若要從舊版的 BizTalk Server 進行移轉，必須將您的結構描述轉換成使用 XSD 而非 XDR。</span><span class="sxs-lookup"><span data-stu-id="d2742-104">If you are migrating from a previous version of BizTalk Server, you must convert your schemas to use XSD rather than XDR.</span></span>  
  
 <span data-ttu-id="d2742-105">您必須執行下列工作，才能將 BizTalk 結構描述從 XDR 語法轉換成 XSD 語法：</span><span class="sxs-lookup"><span data-stu-id="d2742-105">You need to perform the following tasks to convert a BizTalk schema from XDR syntax to XSD syntax:</span></span>  
  
- <span data-ttu-id="d2742-106">變更結構描述檔案 from.xdr to.xsd 的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="d2742-106">Change the extension of the schema file from.xdr to.xsd.</span></span>  
  
- <span data-ttu-id="d2742-107">將重新命名的結構描述新增至適當的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="d2742-107">Add the renamed schema to the appropriate BizTalk project.</span></span>  
  
- <span data-ttu-id="d2742-108">在 [BizTalk 編輯器] 中開啟結構描述，將重新命名的結構描述由 XDR 轉換成 XSD。</span><span class="sxs-lookup"><span data-stu-id="d2742-108">Convert the renamed schema from XDR to XSD by opening the schema in BizTalk Editor.</span></span>  
  
- <span data-ttu-id="d2742-109">儲存該結構描述，以確認永久轉換。</span><span class="sxs-lookup"><span data-stu-id="d2742-109">Make the conversion permanent by saving the schema.</span></span>  
  
  <span data-ttu-id="d2742-110">如需如何執行這些步驟的詳細資訊，請參閱[如何移轉至 XSD 結構描述的 XDR 結構描述](../core/how-to-migrate-xdr-schemas-to-xsd-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="d2742-110">For detailed information about how to perform these steps, see [How to Migrate XDR Schemas to XSD Schemas](../core/how-to-migrate-xdr-schemas-to-xsd-schemas.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2742-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2742-111">See Also</span></span>  
 <span data-ttu-id="d2742-112">[關於結構描述](../core/about-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="d2742-112">[About Schemas](../core/about-schemas.md) </span></span>  
 <span data-ttu-id="d2742-113">[如何將 XDR 結構描述移轉至 XSD 結構描述](../core/how-to-migrate-xdr-schemas-to-xsd-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="d2742-113">[How to Migrate XDR Schemas to XSD Schemas](../core/how-to-migrate-xdr-schemas-to-xsd-schemas.md) </span></span>  
 [<span data-ttu-id="d2742-114">移轉一般檔案記錄</span><span class="sxs-lookup"><span data-stu-id="d2742-114">Migrating Flat File Records</span></span>](../core/migrating-flat-file-records.md)