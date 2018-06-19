---
title: EXECQUERY 陳述式的範例 mySAP 配接器在 BizTalk 中 |Microsoft 文件
description: EXECQUERY 範例和範例使用 mySAP 配接器在 BizTalk 配接器組件 (BAP)
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4139af16-7c38-4ea2-b3e5-5acf8fc1f3c4
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77c5d5877ff502b8fdca620d8b92e4427d3b73b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216238"
---
# <a name="examples-for-execquery-statement"></a><span data-ttu-id="2e357-103">EXECQUERY 陳述式的範例</span><span class="sxs-lookup"><span data-stu-id="2e357-103">Examples for EXECQUERY Statement</span></span>
<span data-ttu-id="2e357-104">本主題提供範例 EXECQUERY 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2e357-104">This topic provides sample EXECQUERY statements.</span></span>  


## <a name="sample-statements"></a><span data-ttu-id="2e357-105">範例陳述式</span><span class="sxs-lookup"><span data-stu-id="2e357-105">Sample statements</span></span>
-   <span data-ttu-id="2e357-106">要執行的查詢，會採用兩個參數 P1 和 P2 命令。</span><span class="sxs-lookup"><span data-stu-id="2e357-106">Command to execute a query that takes two parameters P1 and P2.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = '0000003262',@P2 = 'La Quinta Hotel & Towers'  
    ```  
  
-   <span data-ttu-id="2e357-107">若要執行可採用參數 P1 的值範圍的查詢命令。</span><span class="sxs-lookup"><span data-stu-id="2e357-107">Command to execute a query that takes a range of value for parameter P1.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 BETWEEN '0000003262' AND '0000003265'  
    ```  
  
-   <span data-ttu-id="2e357-108">命令來執行查詢，會使用在特定範圍的參數 P1 的值。</span><span class="sxs-lookup"><span data-stu-id="2e357-108">Command to execute a query that takes values for parameter P1 outside a particular range.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', NOT @P1 BETWEEN '0000003262' AND '0000003265'  
    ```  
  
-   <span data-ttu-id="2e357-109">要執行的查詢，可以採用參數 P1 的兩個值的其中一個命令。</span><span class="sxs-lookup"><span data-stu-id="2e357-109">Command to execute a query that can take one of two values for parameter P1.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = '0000003262', @P1 = '0000003263'  
    ```  
  
-   <span data-ttu-id="2e357-110">要執行的查詢，無法取得參數的特定值的命令。</span><span class="sxs-lookup"><span data-stu-id="2e357-110">Command to execute a query that cannot take specific values for parameters.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', NOT @P1 = '0000003262', NOT @P2 = '0000003263'  
    ```  
  
     <span data-ttu-id="2e357-111">在此範例中，P1 可以有 '0000003262' 以外的任何值。</span><span class="sxs-lookup"><span data-stu-id="2e357-111">In this example, P1 can have any value other than '0000003262'.</span></span> <span data-ttu-id="2e357-112">同樣地，P2 可以有 '0000003263' 以外的任何值。</span><span class="sxs-lookup"><span data-stu-id="2e357-112">Similarly, P2 can have any value other than '0000003263'.</span></span>  
  
-   <span data-ttu-id="2e357-113">要執行具有變體在 SAP 系統中定義的查詢命令。</span><span class="sxs-lookup"><span data-stu-id="2e357-113">Command to execute a query that has variants defined in the SAP system.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @variant = ‘variant1’  
    ```  
  
     <span data-ttu-id="2e357-114">變數是指一組儲存執行 SAP 查詢時，您可以指定的選取準則。</span><span class="sxs-lookup"><span data-stu-id="2e357-114">Variants refer to a saved set of selection criteria that you can specify while executing an SAP query.</span></span> <span data-ttu-id="2e357-115">例如，您可以使用變數來指定查詢的預設值。</span><span class="sxs-lookup"><span data-stu-id="2e357-115">For example, you can use variants to specify default values for queries.</span></span> <span data-ttu-id="2e357-116">對於已定義的所有參數的變異的查詢，您不需要命令文字中指定的參數。</span><span class="sxs-lookup"><span data-stu-id="2e357-116">For queries that have variants defined for all parameters, you do not need to specify the parameters in the command text.</span></span>  
  
-   <span data-ttu-id="2e357-117">要執行的查詢，不需要參數的命令。</span><span class="sxs-lookup"><span data-stu-id="2e357-117">Command to execute a query that does not require a parameter.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = 'some_dummy_value'  
    ```  
  
     <span data-ttu-id="2e357-118">不接受參數的查詢，您必須指定參數使用空值。</span><span class="sxs-lookup"><span data-stu-id="2e357-118">For queries that do not take parameter, you must specify a parameter with a dummy value.</span></span>  
  
-   <span data-ttu-id="2e357-119">執行查詢，其中包含參數，必須是日期值的命令。</span><span class="sxs-lookup"><span data-stu-id="2e357-119">Command to execute a query containing a parameter expecting a date value.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = '20080606'  
    ```  
  
     <span data-ttu-id="2e357-120">對於使用參數必須是日期值的查詢，您必須指定日期為 YYYYMMDD。</span><span class="sxs-lookup"><span data-stu-id="2e357-120">For queries that take parameters expecting date values, you must specify the date as YYYYMMDD.</span></span>  
  
-   <span data-ttu-id="2e357-121">藉由指定參數的 null 值上執行查詢命令。</span><span class="sxs-lookup"><span data-stu-id="2e357-121">Command to execute a query by specifying null values for parameters.</span></span>  
  
     <span data-ttu-id="2e357-122">針對這類的查詢，您無法指定為查詢：</span><span class="sxs-lookup"><span data-stu-id="2e357-122">For such queries, you cannot specify a query as:</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 = 'null'  
    ```  
  
     <span data-ttu-id="2e357-123">相反地，如果您不想指定的值，您不應該指定 P1 完全。</span><span class="sxs-lookup"><span data-stu-id="2e357-123">Instead, if you do not want to specify a value, you should not specify P1 at all.</span></span>  
  
-   <span data-ttu-id="2e357-124">要執行包含參數值必須是大於特定數目的查詢命令。</span><span class="sxs-lookup"><span data-stu-id="2e357-124">Command to execute a query containing a parameter expecting a value greater than a certain number.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 > '0000003262'  
    ```  
  
-   <span data-ttu-id="2e357-125">命令執行查詢，其中包含應為值參數小於特定數目。</span><span class="sxs-lookup"><span data-stu-id="2e357-125">Command to execute a query containing a parameter expecting a value lesser than a certain number.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 < '0000003262'  
    ```  
  
-   <span data-ttu-id="2e357-126">執行查詢，其中包含參數，應為的值大於或等於特定數目的命令。</span><span class="sxs-lookup"><span data-stu-id="2e357-126">Command to execute a query containing a parameter expecting a value greater or equal to a certain number.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 >= '0000003262'  
    ```  
  
-   <span data-ttu-id="2e357-127">執行查詢，其中包含參數，應為的值小於或等於特定數目的命令。</span><span class="sxs-lookup"><span data-stu-id="2e357-127">Command to execute a query containing a parameter expecting a value lesser or equal to a certain number.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 <= '0000003262'  
    ```  
  
-   <span data-ttu-id="2e357-128">執行查詢，其中包含參數，應為的值不等於特定數目的命令。</span><span class="sxs-lookup"><span data-stu-id="2e357-128">Command to execute a query containing a parameter expecting a value not equal to a certain number.</span></span>  
  
    ```  
    EXECQUERY ZTEST3 @USERGROUP='SYSTQV000024', @P1 != '0000003262'  
    ```  
  