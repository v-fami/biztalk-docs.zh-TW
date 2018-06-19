---
title: 部署當地語系化的 BAM XML 檔案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAM, unicode mapping
- unicode mapping [BAM]
ms.assetid: 8e7e3431-cd20-45db-b7f2-0df23e9df42b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3452f13569ca6a0c0bb5843995c07a15b30f4da3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239310"
---
# <a name="deploying-localized-bam-xml-files"></a><span data-ttu-id="1159d-102">部署當地語系化的 BAM XML 檔案</span><span class="sxs-lookup"><span data-stu-id="1159d-102">Deploying Localized BAM XML Files</span></span>
<span data-ttu-id="1159d-103">Microsoft SQL Server Analysis Services 支援 Unicode 對應。</span><span class="sxs-lookup"><span data-stu-id="1159d-103">Microsoft SQL Server Analysis Services supports Unicode mapping.</span></span> <span data-ttu-id="1159d-104">但是，SQL Server Analysis Services 和 Visual Basic 之間 Unicode 的對應，存有已知的字元損毀問題。</span><span class="sxs-lookup"><span data-stu-id="1159d-104">However, there are known character corruption issues with SQL Server Analysis Services and Visual Basic Unicode mapping.</span></span> <span data-ttu-id="1159d-105">特別是從 ANSI 轉換到 Unicode 時，如果地區設定並未設定為正確的當地語系化語言，便會使用錯誤的地區設定資訊進行轉換，因而造成字元損毀。</span><span class="sxs-lookup"><span data-stu-id="1159d-105">Specifically, if the regional settings are not set to the correct localized language when the conversion from ANSI to Unicode occurs, the conversion is performed using the wrong locale information and character corruption occurs.</span></span>  
  
 <span data-ttu-id="1159d-106">為了成功部署 BAM 定義 XML 檔案，您必須先將系統地區設定切換到正確的地區設定，才能實際部署含有當地語系化字元的 BAM 定義 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="1159d-106">To deploy the BAM definition XML file successfully, you must switch your system locale to the correct locale before you can actually deploy a BAM definition XML file that contains localized characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1159d-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1159d-107">See Also</span></span>  
 <span data-ttu-id="1159d-108">[管理 BAM](../core/managing-bam.md) </span><span class="sxs-lookup"><span data-stu-id="1159d-108">[Managing BAM](../core/managing-bam.md) </span></span>  
 [<span data-ttu-id="1159d-109">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="1159d-109">BAM Management Utility</span></span>](../core/bam-management-utility.md)