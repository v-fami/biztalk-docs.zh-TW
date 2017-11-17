---
title: "如何啟用 Analysis Services 與 BAM 主要匯入資料庫之間的加密 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Analysis Services, enabling encryption
- Primary Import database [BAM], SQL Server Analysis Services
- Primary Import database [BAM], enabling encryption
- SQL Server Analysis Services, Primary Import database [BAM]
ms.assetid: 8107c557-e57c-4569-9ff7-abcb7a8e5243
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77069c3690a73957936c786bc05c2690b9df7a10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enable-encryption-between-analysis-services-and-the-bam-primary-import-database"></a><span data-ttu-id="43f8b-102">如何啟用 Analysis Services 與 BAM 主要匯入資料庫之間的加密</span><span class="sxs-lookup"><span data-stu-id="43f8b-102">How to Enable Encryption Between Analysis Services and the BAM Primary Import Database</span></span>
<span data-ttu-id="43f8b-103">安裝或升級 BAM 期間，預設不會啟用加密。</span><span class="sxs-lookup"><span data-stu-id="43f8b-103">Encryption is not enabled by default during an installation or upgrade of BAM.</span></span> <span data-ttu-id="43f8b-104">若要啟用加密，您必須將 BAM 組態 XML 檔案中 UseEncryption 旗標的值設定為 1。</span><span class="sxs-lookup"><span data-stu-id="43f8b-104">To enable encryption, you must set the UseEncryption flag in the BAM configuration XML file to a value of 1.</span></span>  
  
 <span data-ttu-id="43f8b-105">此外，您也必須啟用 SQL Server Analysis Services 中的加密。</span><span class="sxs-lookup"><span data-stu-id="43f8b-105">You must also enable encryption in SQL Server Analysis Services.</span></span> <span data-ttu-id="43f8b-106">如需有關啟用加密的詳細資訊，請參閱[保護與 Analysis Services 執行個體的用戶端通訊](http://go.microsoft.com/fwlink/?LinkId=190805)(http://go.microsoft.com/fwlink/?LinkId=190805)。</span><span class="sxs-lookup"><span data-stu-id="43f8b-106">For more information about enabling encryption, see [Securing Client Communication with an Analysis Services Instance](http://go.microsoft.com/fwlink/?LinkId=190805) (http://go.microsoft.com/fwlink/?LinkId=190805).</span></span>  
  
### <a name="to-enable-encryption-between-sql-server-analysis-services-and-the-bam-primary-import-database"></a><span data-ttu-id="43f8b-107">啟用 SQL Server Analysis Services 與 BAM 主要匯入資料庫之間的加密</span><span class="sxs-lookup"><span data-stu-id="43f8b-107">To enable encryption between SQL Server Analysis Services and the BAM Primary Import Database</span></span>  
  
1.  <span data-ttu-id="43f8b-108">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="43f8b-108">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="43f8b-109">瀏覽至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="43f8b-109">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span></span>  
  
3.  <span data-ttu-id="43f8b-110">型別**bm get-config-FileName:\<輸出檔 >**。</span><span class="sxs-lookup"><span data-stu-id="43f8b-110">Type **bm get-config -FileName:\<output file>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="43f8b-111">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="43f8b-111">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="43f8b-112">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="43f8b-112">Press **ENTER**.</span></span>  
  
5.  <span data-ttu-id="43f8b-113">使用文字編輯器開啟您所匯出的組態檔案，並將 UseEncryption 屬性旗標的值變更為 1。</span><span class="sxs-lookup"><span data-stu-id="43f8b-113">Open the file configuration file that you have exported in a text editor and change the value of the UseEncryption property flag to 1.</span></span>  
  
    -   <span data-ttu-id="43f8b-114">預設值：\<屬性名稱 ="UseEncryption"> 0\</Property ></span><span class="sxs-lookup"><span data-stu-id="43f8b-114">Default Setting: \<Property Name="UseEncryption">0\</Property></span></span>  
  
    -   <span data-ttu-id="43f8b-115">新的設定：\<屬性名稱 ="UseEncryption"> 1\</Property ></span><span class="sxs-lookup"><span data-stu-id="43f8b-115">New Setting: \<Property Name="UseEncryption">1\</Property></span></span>  
  
6.  <span data-ttu-id="43f8b-116">更新 BAM 組態輸入**bm 更新-config-FileName:\<組態檔 >**。</span><span class="sxs-lookup"><span data-stu-id="43f8b-116">Update the BAM configuration by typing **bm update-config -FileName:\<config file>**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="43f8b-117">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="43f8b-117">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43f8b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43f8b-118">See Also</span></span>  
 [<span data-ttu-id="43f8b-119">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="43f8b-119">BAM Management Utility</span></span>](../core/bam-management-utility.md)