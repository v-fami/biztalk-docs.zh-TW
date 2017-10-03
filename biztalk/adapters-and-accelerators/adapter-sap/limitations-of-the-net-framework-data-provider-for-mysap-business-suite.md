---
title: "限制的.NET Framework Data Provider for mySAP Business Suite |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Provider for SAP, limitations of
- .NET Framework Data Provider for mySAP Business Suite, limitations of
ms.assetid: 462e627d-41da-4456-bc62-e8cf7296f5b4
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fd4ad3a57e2b762a53582ceb77eb65f23a535fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="limitations-of-the-net-framework-data-provider-for-mysap-business-suite"></a><span data-ttu-id="4a39b-102">.NET Framework Data Provider for mySAP Business Suite 的限制</span><span class="sxs-lookup"><span data-stu-id="4a39b-102">Limitations of the .NET Framework Data Provider for mySAP Business Suite</span></span>
<span data-ttu-id="4a39b-103">下列已知的限制[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]):</span><span class="sxs-lookup"><span data-stu-id="4a39b-103">The following are known limitations of the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]):</span></span>  
  
-   <span data-ttu-id="4a39b-104">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不支援連接到 SAP 系統，使用安全網路連線 (SNC)。</span><span class="sxs-lookup"><span data-stu-id="4a39b-104">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not support connecting to an SAP system using Secure Network Connection (SNC).</span></span> <span data-ttu-id="4a39b-105">如需 SNC 的詳細資訊，請參閱[SAP 系統與配接器之間的安全性](../../adapters-and-accelerators/adapter-sap/security-between-the-sap-system-and-the-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="4a39b-105">For more information about SNC, see [Security between the SAP system and the adapter](../../adapters-and-accelerators/adapter-sap/security-between-the-sap-system-and-the-adapter.md).</span></span>
  
-   <span data-ttu-id="4a39b-106">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不支援`DbType`或`Size`屬性`SAPParameter`。</span><span class="sxs-lookup"><span data-stu-id="4a39b-106">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not support the `DbType` or `Size` properties of the `SAPParameter`.</span></span> <span data-ttu-id="4a39b-107">相反地，當使用者指定的值時，才`SAPParameter`，值會在內部轉換成根據.NET 和 SAP 資料類型之間建立對應的.NET 資料類型。</span><span class="sxs-lookup"><span data-stu-id="4a39b-107">Instead, when the user specifies a value for the `SAPParameter`, the value is cast internally to a .NET data type according to the established mapping between .NET and SAP data types.</span></span>  
  
-   <span data-ttu-id="4a39b-108">允許的 SAP 資料類型的欄位值的最大長度`CURR`， `DEC`，和`QUAN`是 29 個位數。</span><span class="sxs-lookup"><span data-stu-id="4a39b-108">The maximum length allowed for field values of SAP data types `CURR`, `DEC`, and `QUAN` is 29 digits.</span></span> <span data-ttu-id="4a39b-109">雖然 SAP，這些資料型別值提供 31 位置的原生，但是.NET decimal 資料類型轉換成會施加 29 位數限制。</span><span class="sxs-lookup"><span data-stu-id="4a39b-109">Although SAP provides 31 places for these data-type values natively, the .NET decimal data type to which they are converted imposes a 29-digit limit.</span></span>  
  
-   <span data-ttu-id="4a39b-110">.NET 資料類型之間的對應限制`Double`和 SAP`FLTP`資料型別可能會造成溢位錯誤，當從 SAP 系統的資料讀入的.NET 類型。</span><span class="sxs-lookup"><span data-stu-id="4a39b-110">A mapping limitation between the .NET data type `Double` and the SAP `FLTP` data type can cause an overflow error when reading data from the SAP system into the .NET type.</span></span> <span data-ttu-id="4a39b-111">雖然.NET 類型可以表示成雙精度 64 位元數字值範圍是從負 1.79769313486232 e 308 到正 1.79769313486232 e 308，SAP`FLTP`類型剖析[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不能超過 1.8446744073709552E + 19;有效限制`FLTP`型別是負數 1.8446744073709552E + 到正數 1.8446744073709552E + 19 19 的範圍。</span><span class="sxs-lookup"><span data-stu-id="4a39b-111">Although the .NET type can represent a double-precision 64-bit number with values ranging from negative 1.79769313486232e308 to positive 1.79769313486232e308, an SAP `FLTP` type parsed by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] cannot exceed 1.8446744073709552E+19; the effective limit for the `FLTP` type is the range negative 1.8446744073709552E+19 to positive 1.8446744073709552E+19.</span></span>  
  
-   <span data-ttu-id="4a39b-112">由於處理基礎的用戶端程式庫，逾時問題[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不支援命令，並連接逾時。</span><span class="sxs-lookup"><span data-stu-id="4a39b-112">Due to issues with timeout handling by the underlying client library, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not support command and connection timeout.</span></span>  
  
-   <span data-ttu-id="4a39b-113">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不支援非同步命令的行為。</span><span class="sxs-lookup"><span data-stu-id="4a39b-113">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not support asynchronous command behavior.</span></span>  
  
-   <span data-ttu-id="4a39b-114">使用 SQL Server Integration Services (SSIS) 專案，使用時[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]無法擷取資料行包含的值超過 8000 個字元的資料。</span><span class="sxs-lookup"><span data-stu-id="4a39b-114">When used with a SQL Server Integration Services (SSIS) project, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] fails to retrieve data for columns that contain values with more than 8000 characters.</span></span> <span data-ttu-id="4a39b-115">這是因為，據此 SSIS 限制：</span><span class="sxs-lookup"><span data-stu-id="4a39b-115">This is due to an SSIS restriction according to which:</span></span>  
  
    -   <span data-ttu-id="4a39b-116">不支援大於 4000 個字元，SSIS 變數中的值。</span><span class="sxs-lookup"><span data-stu-id="4a39b-116">Values greater than 4000 characters in SSIS variable are not supported.</span></span>  
  
    -   <span data-ttu-id="4a39b-117">不支援大於 4000 個寬字元的值。</span><span class="sxs-lookup"><span data-stu-id="4a39b-117">Values greater than 4000 wide characters are not supported.</span></span>  
  
    -   <span data-ttu-id="4a39b-118">不支援大於 8000 個單一位元組字元的值。</span><span class="sxs-lookup"><span data-stu-id="4a39b-118">Values greater than 8000 single-byte characters are not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a39b-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a39b-119">See Also</span></span>  
 [<span data-ttu-id="4a39b-120">關於.NET Framework Data Provider for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="4a39b-120">About the .NET Framework Data Provider for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)