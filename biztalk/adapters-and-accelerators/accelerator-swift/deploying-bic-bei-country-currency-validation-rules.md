---
title: "部署驗證 BIC BEI 國家/地區-貨幣規則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e96d416-d5eb-4597-a691-c7dbee33c7d6
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65f1786b37194db25f0e38db7491538857f3406b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-bicbeicountrycurrency-validation-rules"></a><span data-ttu-id="ba79b-102">部署 BIC/BEI/國家/地區/貨幣驗證規則</span><span class="sxs-lookup"><span data-stu-id="ba79b-102">Deploying BIC/BEI/Country/Currency Validation Rules</span></span>
<span data-ttu-id="ba79b-103">**若要部署的 BIC/BEI/國家/地區/貨幣驗證規則：**</span><span class="sxs-lookup"><span data-stu-id="ba79b-103">**To deploy the BIC/BEI/Country/Currency Validation rules:**</span></span>  
  
1.  <span data-ttu-id="ba79b-104">下列的一組原則，%program files%\Microsoft BizTalk Accelerator for SWIFT\SDK\MX Messages\Base 原則，也就是要發行和部署個別的一般和不特定訊息，需要使用商務規則引擎部署精靈。</span><span class="sxs-lookup"><span data-stu-id="ba79b-104">The following set of policies, %program files%\Microsoft BizTalk Accelerator for SWIFT\SDK\MX Messages\Base Policies, which are generic and not message-specific, need to be published and deployed separately using the Business Rule Engine Deployment Wizard.</span></span>  
  
    -   <span data-ttu-id="ba79b-105">MX_BIC_Master_Policy.xml</span><span class="sxs-lookup"><span data-stu-id="ba79b-105">MX_BIC_Master_Policy.xml</span></span>  
  
    -   <span data-ttu-id="ba79b-106">MX_BIC_Validation_Policy.xml</span><span class="sxs-lookup"><span data-stu-id="ba79b-106">MX_BIC_Validation_Policy.xml</span></span>  
  
    -   <span data-ttu-id="ba79b-107">MX_BEI_Validation_Policy.xml</span><span class="sxs-lookup"><span data-stu-id="ba79b-107">MX_BEI_Validation_Policy.xml</span></span>  
  
    -   <span data-ttu-id="ba79b-108">MX_DBConnection_Master_Policy.xml</span><span class="sxs-lookup"><span data-stu-id="ba79b-108">MX_DBConnection_Master_Policy.xml</span></span>  
  
    -   <span data-ttu-id="ba79b-109">MX_BICPlusIBAN_Validation_Policy.xml</span><span class="sxs-lookup"><span data-stu-id="ba79b-109">MX_BICPlusIBAN_Validation_Policy.xml</span></span>  
  
    -   <span data-ttu-id="ba79b-110">MX_SEPA_Validation_Policy.xml</span><span class="sxs-lookup"><span data-stu-id="ba79b-110">MX_SEPA_Validation_Policy.xml</span></span>  
  
2.  <span data-ttu-id="ba79b-111">部署這些原則之前, MX_DBConnection_Master_Policy.xml 和 MX_BIC_Master_Policy.xml 應有資料庫伺服器名稱和資料庫名稱的國家/地區/貨幣值已儲存的位置。</span><span class="sxs-lookup"><span data-stu-id="ba79b-111">Before deploying these policies, MX_DBConnection_Master_Policy.xml and MX_BIC_Master_Policy.xml should have the database server name and database name where the Country/Currency values have been stored.</span></span>  
  
3.  <span data-ttu-id="ba79b-112">一旦已修改的主要原則，發佈所有原則使用商務規則引擎部署精靈 」。</span><span class="sxs-lookup"><span data-stu-id="ba79b-112">Once the master policies have been modified, publish all polices using the Business Rule Engine Deployment Wizard.</span></span> <span data-ttu-id="ba79b-113">使用下列選項： 原則/詞彙檔案匯入資料庫。</span><span class="sxs-lookup"><span data-stu-id="ba79b-113">Use the following option: Import the policy/vocabulary file to database.</span></span>  
  
4.  <span data-ttu-id="ba79b-114">按一下 程式中，按一下 BizTalk Server\<版本 >，按一下 商務規則編輯器，然後部署已發佈的六個原則。</span><span class="sxs-lookup"><span data-stu-id="ba79b-114">Click Programs, click BizTalk Server \<version>, click Business Rule Composer, and then deploy the six published polices.</span></span>