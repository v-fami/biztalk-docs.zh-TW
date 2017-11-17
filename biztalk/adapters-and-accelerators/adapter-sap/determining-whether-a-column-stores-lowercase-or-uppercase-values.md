---
title: "判斷資料行是否儲存大寫或小寫值 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1edc8332-d8c7-4040-895b-f121fb03df44
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93b54c00b43192462fb095dbfbfda4cbf0b248a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="determining-whether-a-column-stores-lowercase-or-uppercase-values"></a><span data-ttu-id="efb10-102">決定是否以值的資料行存放區大寫或小寫</span><span class="sxs-lookup"><span data-stu-id="efb10-102">Determining Whether a Column Stores Lowercase or Uppercase Values</span></span>
<span data-ttu-id="efb10-103">此區段會列出要對 SAP 系統以判定是否 SAP 資料表的資料行儲存大寫或小寫字元的高階工作。</span><span class="sxs-lookup"><span data-stu-id="efb10-103">This section lists high-level tasks to be performed on the SAP system to determine whether a column in an SAP table stores lowercase or uppercase characters.</span></span> <span data-ttu-id="efb10-104">如需詳細指示如何執行這項工作中，您必須連絡您的 SAP 系統管理員，或請參閱 SAP 文件。</span><span class="sxs-lookup"><span data-stu-id="efb10-104">For detailed instructions on how to perform this task you must contact your SAP administrator or refer to SAP documentation.</span></span>  
  
### <a name="to-determine-the-case-of-values-stored-in-a-column"></a><span data-ttu-id="efb10-105">若要判斷值儲存在資料行的大小寫</span><span class="sxs-lookup"><span data-stu-id="efb10-105">To determine the case of values stored in a column</span></span>  
  
1.  <span data-ttu-id="efb10-106">啟動 SAP GUI。</span><span class="sxs-lookup"><span data-stu-id="efb10-106">Start the SAP GUI.</span></span>  
  
2.  <span data-ttu-id="efb10-107">移至交易 SE37，並執行 DDIF_TABL_GET。</span><span class="sxs-lookup"><span data-stu-id="efb10-107">Go to Transaction SE37 and execute DDIF_TABL_GET.</span></span>  
  
3.  <span data-ttu-id="efb10-108">NAME 參數，指定包含您要判斷字元大小寫資訊的資料行的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="efb10-108">For the NAME parameter, specify the table name containing the column for which you want to determine the character case information.</span></span> <span data-ttu-id="efb10-109">例如，KNA1。</span><span class="sxs-lookup"><span data-stu-id="efb10-109">For example, KNA1.</span></span>  
  
4.  <span data-ttu-id="efb10-110">第一個資料表參數是 DD03P_TAB。</span><span class="sxs-lookup"><span data-stu-id="efb10-110">The first table parameter is DD03P_TAB.</span></span> <span data-ttu-id="efb10-111">按一下以查看資料表中的資料列的參數。</span><span class="sxs-lookup"><span data-stu-id="efb10-111">Click the parameter to see the rows in the table.</span></span> <span data-ttu-id="efb10-112">此資料表中的每個資料列對應到資料行 （例如 KNA1) 資料表中指定步驟 3 中。</span><span class="sxs-lookup"><span data-stu-id="efb10-112">Every row in this table corresponds to a column in the table (such as KNA1) you specified in step 3.</span></span>  
  
5.  <span data-ttu-id="efb10-113">在 DD03P_TAB，尋找小寫的資料行，每個資料列中的值。</span><span class="sxs-lookup"><span data-stu-id="efb10-113">In DD03P_TAB, look for the value in the LOWERCASE column for each row.</span></span> <span data-ttu-id="efb10-114">如果小寫的資料行中的值是 'X'，對應的資料行中的資料表 （例如 KNA1)，可將小寫和大寫字元。</span><span class="sxs-lookup"><span data-stu-id="efb10-114">If the value in the LOWERCASE column is 'X', the corresponding column in the table (such as KNA1), can store both lowercase and uppercase characters.</span></span> <span data-ttu-id="efb10-115">小寫的資料行中的值是空的如果對應的資料行只能儲存大寫字元。</span><span class="sxs-lookup"><span data-stu-id="efb10-115">If the value in the LOWERCASE column is empty, the corresponding column can only store uppercase characters.</span></span>  
  
     <span data-ttu-id="efb10-116">例如，名稱資料列的大小寫的資料行是 X。因此，KNA1 的 NAME 資料行可儲存大寫和小寫字元。</span><span class="sxs-lookup"><span data-stu-id="efb10-116">For example, for the NAME row the LOWERCASE column is X. So, the NAME column in KNA1 can store both uppercase and lowercase characters.</span></span> <span data-ttu-id="efb10-117">不過，LAND1 列小寫的資料行是空的。</span><span class="sxs-lookup"><span data-stu-id="efb10-117">However, for the LAND1 row the LOWERCASE column is empty.</span></span> <span data-ttu-id="efb10-118">因此，LAND1 資料表中的資料行 KNA1 只能儲存大寫字元。</span><span class="sxs-lookup"><span data-stu-id="efb10-118">So, the LAND1 column in KNA1 table can only store uppercase characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efb10-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="efb10-119">See Also</span></span>  
 [<span data-ttu-id="efb10-120">使用特定 SAP 配接器實例的 SAP GUI 執行工作</span><span class="sxs-lookup"><span data-stu-id="efb10-120">Performing Tasks Using the SAP GUI for Specific SAP Adapter Scenarios</span></span>](../../adapters-and-accelerators/adapter-sap/performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)