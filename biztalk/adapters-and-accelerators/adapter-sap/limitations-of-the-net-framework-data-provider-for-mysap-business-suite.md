---
title: .NET Framework Data Provider for mySAP Business Suite 的限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Data Provider for SAP, limitations of
- .NET Framework Data Provider for mySAP Business Suite, limitations of
ms.assetid: 462e627d-41da-4456-bc62-e8cf7296f5b4
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9efcf7fb18471c92c504e08df43482fbc64064d2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999815"
---
# <a name="limitations-of-the-net-framework-data-provider-for-mysap-business-suite"></a><span data-ttu-id="4af18-102">.NET Framework Data Provider for mySAP Business Suite 的限制</span><span class="sxs-lookup"><span data-stu-id="4af18-102">Limitations of the .NET Framework Data Provider for mySAP Business Suite</span></span>
<span data-ttu-id="4af18-103">下列已知的限制[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]):</span><span class="sxs-lookup"><span data-stu-id="4af18-103">The following are known limitations of the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]):</span></span>  
  
- <span data-ttu-id="4af18-104">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不支援連接到 SAP 系統，請使用安全網路連線 (SNC)。</span><span class="sxs-lookup"><span data-stu-id="4af18-104">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not support connecting to an SAP system using Secure Network Connection (SNC).</span></span> <span data-ttu-id="4af18-105">如需 SNC 的詳細資訊，請參閱[SAP 系統與配接器之間的安全性](../../adapters-and-accelerators/adapter-sap/security-between-the-sap-system-and-the-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="4af18-105">For more information about SNC, see [Security between the SAP system and the adapter](../../adapters-and-accelerators/adapter-sap/security-between-the-sap-system-and-the-adapter.md).</span></span>
  
- <span data-ttu-id="4af18-106">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] Nepodporuje`DbType`或是`Size`的屬性`SAPParameter`。</span><span class="sxs-lookup"><span data-stu-id="4af18-106">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not support the `DbType` or `Size` properties of the `SAPParameter`.</span></span> <span data-ttu-id="4af18-107">相反地，當使用者指定的值時，才`SAPParameter`，值會在內部根據.NET 和 SAP 資料類型之間建立對應的.NET 資料類型轉換。</span><span class="sxs-lookup"><span data-stu-id="4af18-107">Instead, when the user specifies a value for the `SAPParameter`, the value is cast internally to a .NET data type according to the established mapping between .NET and SAP data types.</span></span>  
  
- <span data-ttu-id="4af18-108">SAP 資料類型的欄位值允許的最大長度`CURR`， `DEC`，和`QUAN`是 29 位數。</span><span class="sxs-lookup"><span data-stu-id="4af18-108">The maximum length allowed for field values of SAP data types `CURR`, `DEC`, and `QUAN` is 29 digits.</span></span> <span data-ttu-id="4af18-109">雖然 SAP，這些資料型別值提供 31 上的芳鄰的原生，轉換成.NET decimal 資料類型會 29 位數限制的大小。</span><span class="sxs-lookup"><span data-stu-id="4af18-109">Although SAP provides 31 places for these data-type values natively, the .NET decimal data type to which they are converted imposes a 29-digit limit.</span></span>  
  
- <span data-ttu-id="4af18-110">.NET 資料類型之間的對應限制`Double`並將 SAP`FLTP`資料型別可能會導致溢位錯誤，當從 SAP 系統的資料讀入的.NET 類型。</span><span class="sxs-lookup"><span data-stu-id="4af18-110">A mapping limitation between the .NET data type `Double` and the SAP `FLTP` data type can cause an overflow error when reading data from the SAP system into the .NET type.</span></span> <span data-ttu-id="4af18-111">雖然.NET 型別可以代表雙精確度 64 位元數字值範圍從負 1.79769313486232e308 到正 1.79769313486232 e 308，SAP`FLTP`型別剖析[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不能超過 1.8446744073709552E + 19;有效限制`FLTP`型別是負的 1.8446744073709552E + 19 到正數 1.8446744073709552E + 19 的範圍。</span><span class="sxs-lookup"><span data-stu-id="4af18-111">Although the .NET type can represent a double-precision 64-bit number with values ranging from negative 1.79769313486232e308 to positive 1.79769313486232e308, an SAP `FLTP` type parsed by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] cannot exceed 1.8446744073709552E+19; the effective limit for the `FLTP` type is the range negative 1.8446744073709552E+19 to positive 1.8446744073709552E+19.</span></span>  
  
- <span data-ttu-id="4af18-112">因為處理基礎的用戶端程式庫，逾時問題而[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不支援命令，並連接逾時。</span><span class="sxs-lookup"><span data-stu-id="4af18-112">Due to issues with timeout handling by the underlying client library, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not support command and connection timeout.</span></span>  
  
- <span data-ttu-id="4af18-113">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]不支援非同步命令的行為。</span><span class="sxs-lookup"><span data-stu-id="4af18-113">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not support asynchronous command behavior.</span></span>  
  
- <span data-ttu-id="4af18-114">SQL Server Integration Services (SSIS) 專案中，搭配使用時[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]無法擷取資料行包含值超過 8000 個字元的資料。</span><span class="sxs-lookup"><span data-stu-id="4af18-114">When used with a SQL Server Integration Services (SSIS) project, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] fails to retrieve data for columns that contain values with more than 8000 characters.</span></span> <span data-ttu-id="4af18-115">這是因為，據此 SSIS 限制：</span><span class="sxs-lookup"><span data-stu-id="4af18-115">This is due to an SSIS restriction according to which:</span></span>  
  
  -   <span data-ttu-id="4af18-116">不支援大於 4000 個字元，SSIS 變數中的值。</span><span class="sxs-lookup"><span data-stu-id="4af18-116">Values greater than 4000 characters in SSIS variable are not supported.</span></span>  
  
  -   <span data-ttu-id="4af18-117">不支援大於 4000 個寬字元的值。</span><span class="sxs-lookup"><span data-stu-id="4af18-117">Values greater than 4000 wide characters are not supported.</span></span>  
  
  -   <span data-ttu-id="4af18-118">不支援大於 8000 個單一位元組字元的值。</span><span class="sxs-lookup"><span data-stu-id="4af18-118">Values greater than 8000 single-byte characters are not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4af18-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4af18-119">See Also</span></span>  
 [<span data-ttu-id="4af18-120">關於 .NET Framework Data Provider for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="4af18-120">About the .NET Framework Data Provider for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)