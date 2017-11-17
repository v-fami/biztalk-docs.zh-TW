---
title: "限制 BizTalk adapter for SQL Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a19b109-a6b7-452f-a544-48627fa52f36
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5a80990a9e3f417b64a06d8823300d53b2c4f3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="limitations-of-biztalk-adapter-for-sql-server"></a><span data-ttu-id="a4726-102">BizTalk adapter for SQL Server 的限制</span><span class="sxs-lookup"><span data-stu-id="a4726-102">Limitations of BizTalk Adapter for SQL Server</span></span>
<span data-ttu-id="a4726-103">下列已知限制[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="a4726-103">The following are known limitations for [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]:</span></span>  
  
-   <span data-ttu-id="a4726-104">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]不支援 SQL Server 資料庫中建立同義字。</span><span class="sxs-lookup"><span data-stu-id="a4726-104">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not support synonyms created in the SQL Server database.</span></span> <span data-ttu-id="a4726-105">SQL Server 中的同義字的相關資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=120111](http://go.microsoft.com/fwlink/?LinkId=120111)。</span><span class="sxs-lookup"><span data-stu-id="a4726-105">For information about synonyms in SQL Server, see [http://go.microsoft.com/fwlink/?LinkId=120111](http://go.microsoft.com/fwlink/?LinkId=120111).</span></span>  
  
-   <span data-ttu-id="a4726-106">如果您變更執行的電腦的系統時間[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]主機，時間不會自動更新中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]主機。</span><span class="sxs-lookup"><span data-stu-id="a4726-106">If you change the system time of the computer running the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] host, the time is not updated automatically in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] host.</span></span> <span data-ttu-id="a4726-107">這可能會導致不正確的行為，使用的接收埠的輸入作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a4726-107">This could lead to incorrect behavior of the inbound operations that use the receive port of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="a4726-108">因應措施，您必須重新啟動後已變更其執行之電腦的系統時間有接收埠的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="a4726-108">As a workaround, you must restart the host instance that has a receive port after you have changed the system time of the computer running it.</span></span>  
  
-   <span data-ttu-id="a4726-109">如果預存程序中的參數名稱包含 127 或多個字元，則無法執行預存程序使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a4726-109">If a parameter name in a stored procedure contains 127 or more characters, you cannot execute the stored procedure using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="a4726-110">這是因為 ADO.NET 的限制。</span><span class="sxs-lookup"><span data-stu-id="a4726-110">This is due to the limitation of ADO.NET.</span></span>  
  
-   <span data-ttu-id="a4726-111">WSDL[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]產生，轉換為 proxy 時，會公開為 System.DateTime DateTimeOffset 資料行。</span><span class="sxs-lookup"><span data-stu-id="a4726-111">The WSDL the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] generates, when converted to a proxy, exposes the DateTimeOffset column as System.DateTime.</span></span> <span data-ttu-id="a4726-112">此資料類型無法儲存時區資訊。</span><span class="sxs-lookup"><span data-stu-id="a4726-112">This data type cannot store time zone information.</span></span> <span data-ttu-id="a4726-113">因此，配接器傳送到 proxy 的任何日期/時間值會轉換成.NET 應用程式中的本機時間。</span><span class="sxs-lookup"><span data-stu-id="a4726-113">As a consequence, any date/time value the adapter sends to the proxy will be converted into local time in the .NET application.</span></span> <span data-ttu-id="a4726-114">如果您想要保留的時區資訊，您必須變更您的 proxy 使用 String 型別，而不是 System.DateTime 的介面。</span><span class="sxs-lookup"><span data-stu-id="a4726-114">If you wish to keep the time zone information, you must change the interface of your proxy to use the String type instead of System.DateTime.</span></span> <span data-ttu-id="a4726-115">然後，使用 XmlConvert.ToDateTimeOffset 建立 Sytstem.DateTimeOffset 物件，它可以儲存時區資訊。</span><span class="sxs-lookup"><span data-stu-id="a4726-115">Then, use XmlConvert.ToDateTimeOffset to create a Sytstem.DateTimeOffset object, which can store the timezone information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4726-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4726-116">See Also</span></span>  
 [<span data-ttu-id="a4726-117">瞭解 BizTalk Adapter for SQL Server</span><span class="sxs-lookup"><span data-stu-id="a4726-117">UNderstand BizTalk Adapter for SQL Server</span></span>](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)