---
title: 函式和 Oracle 資料庫中的記錄類型的程序上的作業 |Microsoft 文件
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
ms.openlocfilehash: 46daadeaa5d1fc1060217f044a9d143488c38d7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-functions-and-procedures-with-record-types-in-oracle-database"></a><span data-ttu-id="f8911-102">函數和程序與 Oracle 資料庫中的記錄類型的作業</span><span class="sxs-lookup"><span data-stu-id="f8911-102">Operations on Functions and Procedures with RECORD Types in Oracle Database</span></span>
<span data-ttu-id="f8911-103">Oracle 記錄類型可用來代表階層式參數傳遞至 PL/SQL 函數和程序中的資訊。</span><span class="sxs-lookup"><span data-stu-id="f8911-103">Oracle RECORD types are used to represent hierarchical information in parameters passed to PL/SQL functions and procedures.</span></span> <span data-ttu-id="f8911-104">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現記錄類型為複雜的 XML 型別。</span><span class="sxs-lookup"><span data-stu-id="f8911-104">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces RECORD types as complex XML types.</span></span> <span data-ttu-id="f8911-105">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援下列幾種記錄類型：</span><span class="sxs-lookup"><span data-stu-id="f8911-105">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports the following kinds of RECORD types:</span></span>  
  
-   <span data-ttu-id="f8911-106">記錄會宣告為預存程序和函式中的資料表 %資料列型別參數的類型。</span><span class="sxs-lookup"><span data-stu-id="f8911-106">RECORD types that are declared as TABLE%ROWTYPE parameters in stored procedures and functions.</span></span>  
  
-   <span data-ttu-id="f8911-107">例如，宣告類型的記錄中當做參數的 PL/SQL 封裝的記錄類型輸入 rec_type1 是 RECORD(name varchar2(100), age number(3));</span><span class="sxs-lookup"><span data-stu-id="f8911-107">RECORD types that are declared as TYPE of RECORD parameters in PL/SQL packages for example, TYPE rec_type1 IS RECORD(name varchar2(100), age number(3));</span></span>  
  
-   <span data-ttu-id="f8911-108">包含巢狀的記錄的記錄類型。</span><span class="sxs-lookup"><span data-stu-id="f8911-108">RECORD types that contain nested records.</span></span>  
  
-   <span data-ttu-id="f8911-109">記錄中出現的類型為，逾時或在 OUT 參數的程序或函式。</span><span class="sxs-lookup"><span data-stu-id="f8911-109">RECORD types that appear as IN, OUT, or IN OUT parameters to procedures or functions.</span></span>  
  
-   <span data-ttu-id="f8911-110">傳回值的函式的記錄類型。</span><span class="sxs-lookup"><span data-stu-id="f8911-110">RECORD types that are RETURN values of functions.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8911-111">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]不支援 BFILE 做為記錄成員的類型。</span><span class="sxs-lookup"><span data-stu-id="f8911-111">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support BFILE types as RECORD members.</span></span>  
  
 <span data-ttu-id="f8911-112">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="f8911-112">For information about:</span></span>  
  
-   <span data-ttu-id="f8911-113">叫用函式或程序牽涉到使用 WCF 服務模型的記錄類型，請參閱[執行作業使用記錄類型在 Oracle 資料庫中使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="f8911-113">Invoking a function or procedure involving RECORD types using the WCF service model, see [Run Operations Using RECORD Types in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
-   <span data-ttu-id="f8911-114">叫用函式或程序涉及記錄類型使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[叫用函式和程序的記錄類型所使用的 BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-functions-and-procedures-with-record-types-in-oracle-db-with-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f8911-114">Invoking a function or procedure involving RECORD types using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Invoke Functions and Procedures with RECORD Types by Using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-functions-and-procedures-with-record-types-in-oracle-db-with-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="f8911-115">記錄的 XML 結構類型支援的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[記錄類型的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-record-types.md)。</span><span class="sxs-lookup"><span data-stu-id="f8911-115">XML structure for RECORD types as supported by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Message Schemas for RECORD Types](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-record-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8911-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8911-116">See Also</span></span>  
 <span data-ttu-id="f8911-117">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="f8911-117">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>