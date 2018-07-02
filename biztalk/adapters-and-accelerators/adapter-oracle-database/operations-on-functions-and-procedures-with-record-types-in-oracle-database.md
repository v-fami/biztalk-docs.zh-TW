---
title: 函式和含有 RECORD 類型在 Oracle 資料庫中的程序作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RECORD type
ms.assetid: 28ecb76c-de82-43df-83cc-917c482417b3
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2635ac4b21173fe1a12603c60263dfa70b5a18e5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974199"
---
# <a name="operations-on-functions-and-procedures-with-record-types-in-oracle-database"></a><span data-ttu-id="67fbf-102">函式和含有 RECORD 類型在 Oracle 資料庫中的程序作業</span><span class="sxs-lookup"><span data-stu-id="67fbf-102">Operations on Functions and Procedures with RECORD Types in Oracle Database</span></span>
<span data-ttu-id="67fbf-103">Oracle 記錄類型用來代表階層式參數傳遞至 PL/SQL 函數與程序中的資訊。</span><span class="sxs-lookup"><span data-stu-id="67fbf-103">Oracle RECORD types are used to represent hierarchical information in parameters passed to PL/SQL functions and procedures.</span></span> <span data-ttu-id="67fbf-104">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現複雜的 XML 類型的記錄類型。</span><span class="sxs-lookup"><span data-stu-id="67fbf-104">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces RECORD types as complex XML types.</span></span> <span data-ttu-id="67fbf-105">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援下列幾種記錄類型：</span><span class="sxs-lookup"><span data-stu-id="67fbf-105">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports the following kinds of RECORD types:</span></span>  
  
- <span data-ttu-id="67fbf-106">記錄會宣告為預存程序和函式中的資料表 %資料列型別參數的類型。</span><span class="sxs-lookup"><span data-stu-id="67fbf-106">RECORD types that are declared as TABLE%ROWTYPE parameters in stored procedures and functions.</span></span>  
  
- <span data-ttu-id="67fbf-107">例如，宣告為類型的記錄參數的 PL/SQL 封裝中的記錄類型輸入 rec_type1 是 RECORD(name varchar2(100), age number(3));</span><span class="sxs-lookup"><span data-stu-id="67fbf-107">RECORD types that are declared as TYPE of RECORD parameters in PL/SQL packages for example, TYPE rec_type1 IS RECORD(name varchar2(100), age number(3));</span></span>  
  
- <span data-ttu-id="67fbf-108">包含巢狀的記錄的記錄類型。</span><span class="sxs-lookup"><span data-stu-id="67fbf-108">RECORD types that contain nested records.</span></span>  
  
- <span data-ttu-id="67fbf-109">記錄中出現的類型為，縮小或在 OUT 參數至程序或函式。</span><span class="sxs-lookup"><span data-stu-id="67fbf-109">RECORD types that appear as IN, OUT, or IN OUT parameters to procedures or functions.</span></span>  
  
- <span data-ttu-id="67fbf-110">是函式傳回值的記錄類型。</span><span class="sxs-lookup"><span data-stu-id="67fbf-110">RECORD types that are RETURN values of functions.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="67fbf-111">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] Nepodporuje BFILE 做為記錄成員的類型。</span><span class="sxs-lookup"><span data-stu-id="67fbf-111">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support BFILE types as RECORD members.</span></span>  
  
  <span data-ttu-id="67fbf-112">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="67fbf-112">For information about:</span></span>  
  
- <span data-ttu-id="67fbf-113">叫用函式或程序牽涉到使用 WCF 服務模型的記錄類型，請參閱[執行作業使用記錄類型在 Oracle 資料庫中使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="67fbf-113">Invoking a function or procedure involving RECORD types using the WCF service model, see [Run Operations Using RECORD Types in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
- <span data-ttu-id="67fbf-114">叫用函式或程序涉及記錄型別使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 叫用函式和程序的記錄類型，使用 BizTalk server](../../adapters-and-accelerators/adapter-oracle-database/run-functions-and-procedures-with-record-types-in-oracle-db-with-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="67fbf-114">Invoking a function or procedure involving RECORD types using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Invoke Functions and Procedures with RECORD Types by Using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-functions-and-procedures-with-record-types-in-oracle-db-with-biztalk-server.md).</span></span>  
  
- <span data-ttu-id="67fbf-115">記錄的 XML 結構類型所支援之[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱 <<c2> [ 記錄類型的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-record-types.md)。</span><span class="sxs-lookup"><span data-stu-id="67fbf-115">XML structure for RECORD types as supported by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Message Schemas for RECORD Types](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-record-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67fbf-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67fbf-116">See Also</span></span>  
 <span data-ttu-id="67fbf-117">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="67fbf-117">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>