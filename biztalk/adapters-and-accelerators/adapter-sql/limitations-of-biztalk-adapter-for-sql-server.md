---
title: BizTalk Adapter for SQL Server 的限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a19b109-a6b7-452f-a544-48627fa52f36
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 195701e4bba469a7faaab36a5ae1636c5abca5f4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967383"
---
# <a name="limitations-of-biztalk-adapter-for-sql-server"></a><span data-ttu-id="f43ec-102">BizTalk Adapter for SQL Server 的限制</span><span class="sxs-lookup"><span data-stu-id="f43ec-102">Limitations of BizTalk Adapter for SQL Server</span></span>
<span data-ttu-id="f43ec-103">下列已知限制[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="f43ec-103">The following are known limitations for [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]:</span></span>  
  
- <span data-ttu-id="f43ec-104">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]不支援在 SQL Server 資料庫中建立的同義字。</span><span class="sxs-lookup"><span data-stu-id="f43ec-104">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not support synonyms created in the SQL Server database.</span></span> <span data-ttu-id="f43ec-105">SQL Server 中的同義字的相關資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkId=120111 ](http://go.microsoft.com/fwlink/?LinkId=120111)。</span><span class="sxs-lookup"><span data-stu-id="f43ec-105">For information about synonyms in SQL Server, see [http://go.microsoft.com/fwlink/?LinkId=120111](http://go.microsoft.com/fwlink/?LinkId=120111).</span></span>  
  
- <span data-ttu-id="f43ec-106">如果您變更執行的電腦的系統時間[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]主機，時間不會自動更新在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]主應用程式。</span><span class="sxs-lookup"><span data-stu-id="f43ec-106">If you change the system time of the computer running the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] host, the time is not updated automatically in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] host.</span></span> <span data-ttu-id="f43ec-107">這可能會導致不正確的行為，使用的接收埠的輸入作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f43ec-107">This could lead to incorrect behavior of the inbound operations that use the receive port of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="f43ec-108">因應措施，您必須重新啟動主控件執行個體，您已變更執行它的電腦的系統時間之後的接收埠。</span><span class="sxs-lookup"><span data-stu-id="f43ec-108">As a workaround, you must restart the host instance that has a receive port after you have changed the system time of the computer running it.</span></span>  
  
- <span data-ttu-id="f43ec-109">如果預存程序中的參數名稱不可超過 127 個以上的字元，您無法執行預存程序使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f43ec-109">If a parameter name in a stored procedure contains 127 or more characters, you cannot execute the stored procedure using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="f43ec-110">這是因為 ADO.NET 的限制。</span><span class="sxs-lookup"><span data-stu-id="f43ec-110">This is due to the limitation of ADO.NET.</span></span>  
  
- <span data-ttu-id="f43ec-111">WSDL[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]產生時，轉換為 proxy 時，會公開為 System.DateTime 的 DateTimeOffset 資料行。</span><span class="sxs-lookup"><span data-stu-id="f43ec-111">The WSDL the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] generates, when converted to a proxy, exposes the DateTimeOffset column as System.DateTime.</span></span> <span data-ttu-id="f43ec-112">此資料類型無法儲存時區資訊。</span><span class="sxs-lookup"><span data-stu-id="f43ec-112">This data type cannot store time zone information.</span></span> <span data-ttu-id="f43ec-113">如此一來，配接器傳送至 proxy 的任何日期/時間值會轉換成.NET 應用程式中的當地時間。</span><span class="sxs-lookup"><span data-stu-id="f43ec-113">As a consequence, any date/time value the adapter sends to the proxy will be converted into local time in the .NET application.</span></span> <span data-ttu-id="f43ec-114">如果您想要保留的時區資訊，您必須變更您的 proxy，而不是 System.DateTime 使用字串類型的介面。</span><span class="sxs-lookup"><span data-stu-id="f43ec-114">If you wish to keep the time zone information, you must change the interface of your proxy to use the String type instead of System.DateTime.</span></span> <span data-ttu-id="f43ec-115">然後，使用 XmlConvert.ToDateTimeOffset 建立 Sytstem.DateTimeOffset 物件，它可以儲存時區資訊。</span><span class="sxs-lookup"><span data-stu-id="f43ec-115">Then, use XmlConvert.ToDateTimeOffset to create a Sytstem.DateTimeOffset object, which can store the timezone information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f43ec-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f43ec-116">See Also</span></span>  
 [<span data-ttu-id="f43ec-117">了解 BizTalk Adapter for SQL Server</span><span class="sxs-lookup"><span data-stu-id="f43ec-117">UNderstand BizTalk Adapter for SQL Server</span></span>](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)