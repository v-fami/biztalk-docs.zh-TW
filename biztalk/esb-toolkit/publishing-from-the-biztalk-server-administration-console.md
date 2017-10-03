---
title: "從 BizTalk Server 管理主控台中發行 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b78b1981-b227-4cf5-9435-6fc57963552a
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 313bfb773a94914ed9bebd3930dfd0033ecf4ac3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="publishing-from-the-biztalk-server-administration-console"></a><span data-ttu-id="83207-102">從 BizTalk Server 管理主控台中發行</span><span class="sxs-lookup"><span data-stu-id="83207-102">Publishing from the BizTalk Server Administration Console</span></span>
<span data-ttu-id="83207-103">如果您想要管理透過端點發行[!INCLUDE[prague](../includes/prague-md.md)]而不是在 ESB 管理入口網站管理主控台中，您可以在的 [描述] 欄位中輸入通用描述、 探索與整合 (UDDI) moniker若要發行至 UDDI 的端點。</span><span class="sxs-lookup"><span data-stu-id="83207-103">If you want to manage endpoint publishing through the [!INCLUDE[prague](../includes/prague-md.md)] Administration Console instead of the ESB Management Portal, you can do so by entering a Universal Description, Discovery, and Integration (UDDI) moniker in the description field of the endpoints to publish to UDDI.</span></span> <span data-ttu-id="83207-104">以下是範例 moniker。</span><span class="sxs-lookup"><span data-stu-id="83207-104">The following is an example moniker.</span></span>  
  
```  
uddi://TransportType=other;Status=Published.  
```  
  
 <span data-ttu-id="83207-105">您可以設定下列的 UDDI 屬性使用**描述**欄位[!INCLUDE[prague](../includes/prague-md.md)]管理主控台：</span><span class="sxs-lookup"><span data-stu-id="83207-105">You can set the following UDDI properties using the **Description** field in the [!INCLUDE[prague](../includes/prague-md.md)] Administration Console:</span></span>  
  
-   <span data-ttu-id="83207-106">**ModifiedBy**。</span><span class="sxs-lookup"><span data-stu-id="83207-106">**ModifiedBy**.</span></span> <span data-ttu-id="83207-107">此選擇性屬性包含修改端點; 的使用者帳戶名稱例如，MyDomainName\MyUserName。</span><span class="sxs-lookup"><span data-stu-id="83207-107">This optional property contains the account name of the user that modified the endpoint; for example, MyDomainName\MyUserName.</span></span>  
  
-   <span data-ttu-id="83207-108">**UDDIContact**。</span><span class="sxs-lookup"><span data-stu-id="83207-108">**UDDIContact**.</span></span> <span data-ttu-id="83207-109">此選用性屬性是使用者的定義為 UDDI 的商業提供者的連絡人名稱。</span><span class="sxs-lookup"><span data-stu-id="83207-109">This optional property is the contact name of the user defined for the UDDI Business Provider.</span></span>  
  
-   <span data-ttu-id="83207-110">**UDDIUserType**。</span><span class="sxs-lookup"><span data-stu-id="83207-110">**UDDIUserType**.</span></span> <span data-ttu-id="83207-111">此選用性屬性是使用者的定義為 UDDI 的商業提供者的使用者類型。</span><span class="sxs-lookup"><span data-stu-id="83207-111">This optional property is the user type of the user defined for the UDDI Business Provider.</span></span>  
  
-   <span data-ttu-id="83207-112">**UDDIEmail**。</span><span class="sxs-lookup"><span data-stu-id="83207-112">**UDDIEmail**.</span></span> <span data-ttu-id="83207-113">此選用性屬性是使用者的定義為 UDDI 的商業提供者電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="83207-113">This optional property is the e-mail address of the user defined for the UDDI Business Provider.</span></span>  
  
-   <span data-ttu-id="83207-114">**TransportType**。</span><span class="sxs-lookup"><span data-stu-id="83207-114">**TransportType**.</span></span> <span data-ttu-id="83207-115">此選用性屬性是端點配接器類型，例如**檔案、 MQS、 Wcf-wshttp、 SOAP、 HTTP、**或**FTP**。</span><span class="sxs-lookup"><span data-stu-id="83207-115">This optional property is the endpoint adapter type, such as **FILE, MQS, WCF-WsHttp, SOAP, HTTP,** or **FTP**.</span></span>  
  
-   <span data-ttu-id="83207-116">**狀態**。</span><span class="sxs-lookup"><span data-stu-id="83207-116">**Status**.</span></span> <span data-ttu-id="83207-117">此選用性屬性是狀態的端點，例如**發佈**或**暫止**。</span><span class="sxs-lookup"><span data-stu-id="83207-117">This optional property is the status of the endpoint, such as **Published** or **Pending**.</span></span> <span data-ttu-id="83207-118">UDDI 發行服務會使用此屬性以探索端點的狀態。</span><span class="sxs-lookup"><span data-stu-id="83207-118">The UDDI Publishing Service uses this attribute to discover the status of the endpoint.</span></span>  
  
-   <span data-ttu-id="83207-119">**BindingType**。</span><span class="sxs-lookup"><span data-stu-id="83207-119">**BindingType**.</span></span> <span data-ttu-id="83207-120">此選擇性屬性為特定的通訊協定 （URL 類型） 的 UDDI 繫結支援，例如**mailto、 http、 https、 ftp、 傳真、 phone**或**其他**。</span><span class="sxs-lookup"><span data-stu-id="83207-120">This optional property is the specific protocol (URL Type) that the UDDI binding supports, such as **mailto, http, https, ftp, fax, phone,** or **other**.</span></span> <span data-ttu-id="83207-121">UDDI 發行服務會使用這個屬性，來建立端點的繫結。</span><span class="sxs-lookup"><span data-stu-id="83207-121">The UDDI Publishing Service uses this attribute to create the endpoint binding.</span></span>