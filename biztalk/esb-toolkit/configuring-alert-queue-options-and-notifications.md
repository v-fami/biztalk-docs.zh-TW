---
title: "設定警示的佇列選項和通知 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f78afbf9-6e27-4887-8424-f265fbd8448a
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 914af88b989c73444e16acedf43b9a236897859d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-alert-queue-options-and-notifications"></a><span data-ttu-id="f43b5-102">設定警示的佇列選項和通知</span><span class="sxs-lookup"><span data-stu-id="f43b5-102">Configuring Alert Queue Options and Notifications</span></span>
<span data-ttu-id="f43b5-103">ESB 管理入口網站會產生警示的錯誤訊息抵達入口網站中，以及它使用 ESB 通知服務佇列，並將警示通知傳送給訂閱警示的使用者使用 ESB 警示服務。</span><span class="sxs-lookup"><span data-stu-id="f43b5-103">The ESB Management Portal uses the ESB Alert Service to generate alerts as fault messages arrive at the portal, and it uses the ESB Notification Service to queue and send alert notifications to users that subscribe to alerts.</span></span> <span data-ttu-id="f43b5-104">您可以編輯這些 ESB 管理入口網站中的服務所使用的設定。</span><span class="sxs-lookup"><span data-stu-id="f43b5-104">You can edit the settings used by these services in the ESB Management Portal.</span></span>  
  
### <a name="to-configure-the-settings-for-the-esb-alert-service"></a><span data-ttu-id="f43b5-105">若要設定 ESB 警示服務的設定</span><span class="sxs-lookup"><span data-stu-id="f43b5-105">To configure the settings for the ESB Alert Service</span></span>  
  
1.  <span data-ttu-id="f43b5-106">請確定您在入口網站使用 （入口網站管理員的自動成員） 的 Microsoft BizTalk Server 系統管理員帳戶群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="f43b5-106">Ensure that you log on to the portal using an account that is a member of the Microsoft BizTalk Server Administrators account group (of which portal administrators are automatically a member).</span></span>  
  
2.  <span data-ttu-id="f43b5-107">指向**Admin**入口網站的主功能表上的索引標籤，然後按一下 [**錯誤設定**開啟入口網站[錯誤設定] 頁面](../esb-toolkit/fault-settings-page.md)。</span><span class="sxs-lookup"><span data-stu-id="f43b5-107">Point to the **Admin** tab on the portal main menu, and then click **Fault Settings** to open the portal [Fault Settings Page](../esb-toolkit/fault-settings-page.md).</span></span>  
  
3.  <span data-ttu-id="f43b5-108">在**警示佇列選項**區段中，選取或清除**啟用警示的佇列服務**核取方塊以啟用或停用服務。</span><span class="sxs-lookup"><span data-stu-id="f43b5-108">In the **Alert Queue Options** section, select or clear the **Enable Alert Queue Service** check box to enable or disable the service.</span></span>  
  
4.  <span data-ttu-id="f43b5-109">如果您啟用此服務時，編輯以符合我們的需求剩餘的控制項中的值。</span><span class="sxs-lookup"><span data-stu-id="f43b5-109">If you enable the service, edit the values in the remaining controls to suit our requirements.</span></span> <span data-ttu-id="f43b5-110">與 Microsoft Active Directory 的服務互動，因此您必須指定適當的 LDAP （輕量型目錄存取通訊協定） 連接字串。</span><span class="sxs-lookup"><span data-stu-id="f43b5-110">The service interacts with Microsoft Active Directory, so you must specify the appropriate LDAP (Lightweight Directory Access Protocol) connection string.</span></span> <span data-ttu-id="f43b5-111">您也可以指定佇列的批次大小和輪詢間隔。</span><span class="sxs-lookup"><span data-stu-id="f43b5-111">You can also specify the queue batch size and polling interval.</span></span>  
  
5.  <span data-ttu-id="f43b5-112">按一下**儲存**儲存新的設定。</span><span class="sxs-lookup"><span data-stu-id="f43b5-112">Click **Save** to save the new settings.</span></span>  
  
### <a name="to-configure-the-settings-for-the-esb-alert-email-notification-service"></a><span data-ttu-id="f43b5-113">若要設定 ESB 警示的電子郵件通知服務的設定</span><span class="sxs-lookup"><span data-stu-id="f43b5-113">To configure the settings for the ESB Alert Email Notification service</span></span>  
  
1.  <span data-ttu-id="f43b5-114">請確定您在入口網站使用 （入口網站管理員的自動成員） 的 BizTalk Server 系統管理員帳戶群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="f43b5-114">Ensure that you log on to the portal using an account that is a member of the BizTalk Server Administrators account group (of which portal administrators are automatically a member).</span></span>  
  
2.  <span data-ttu-id="f43b5-115">指向**Admin**入口網站的主功能表上的索引標籤，然後按一下 [**錯誤設定**開啟入口網站[錯誤設定] 頁面](../esb-toolkit/fault-settings-page.md)。</span><span class="sxs-lookup"><span data-stu-id="f43b5-115">Point to the **Admin** tab on the portal main menu, and then click **Fault Settings** to open the portal [Fault Settings Page](../esb-toolkit/fault-settings-page.md).</span></span>  
  
3.  <span data-ttu-id="f43b5-116">在**警示的電子郵件選項**區段中，選取或清除**啟用警示的電子郵件服務**核取方塊以啟用或停用服務。</span><span class="sxs-lookup"><span data-stu-id="f43b5-116">In the **Alert Email Options** section, select or clear the **Enable Alert Email Service** check box to enable or disable the service.</span></span>  
  
4.  <span data-ttu-id="f43b5-117">如果您啟用此服務時，編輯以符合我們的需求剩餘的控制項中的值。</span><span class="sxs-lookup"><span data-stu-id="f43b5-117">If you enable the service, edit the values in the remaining controls to suit our requirements.</span></span> <span data-ttu-id="f43b5-118">指定電子郵件伺服器名稱和 「 寄件者 」 地址變更，視需要輪詢間隔與批次大小，指定服務所使用的可延伸樣式表語言轉換 (XSLT) 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="f43b5-118">Specify the e-mail server name and the "from" address, change the polling interval and batch size as required, and specify the path to Extensible Stylesheet Language Transformations (XSLT) files that the service uses.</span></span>  
  
5.  <span data-ttu-id="f43b5-119">按一下**儲存**儲存新的設定。</span><span class="sxs-lookup"><span data-stu-id="f43b5-119">Click **Save** to save the new settings.</span></span>