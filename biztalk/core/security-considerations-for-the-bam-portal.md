---
title: "BAM 入口網站的安全性考量 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM portal, security
- BAM portal, administrator accounts
- user accounts, BAM
- administrator accounts, BAM portal
- BAM portal, user accounts
- security, BAM portal
ms.assetid: 5c8e6034-dfb8-4dba-b040-0c19504abdb2
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b0f5220eba5b66daf41dffc7ab74f93df8bb509
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="security-considerations-for-the-bam-portal"></a>BAM 入口網站的安全性考量
依照最低權限原則，應對使用 BAM 入口網站執行例行工作的使用者帳戶賦予嚴格的存取權限。 當您設定 BAM 的使用者帳戶時，請記住下列重點，以便在安全性與使用者之適當存取權之間取得平衡。  
  
## <a name="user-accounts"></a>使用者帳戶  
 不能使用 BAM 入口網站的分散式的 navigationfeature 具有最小權限的使用者帳戶。 若要能夠使用此功能，這些帳戶必須有足夠的權限，可以同時從遠端電腦和本機電腦存取 Web 服務。  
  
 BAM Web 服務的使用者帳戶必須對所有的參考資料庫擁有存取權限，而且必須是參考資料庫的 BAM_ManagementWS 角色成員。  
  
 對於下列使用者類型，請特別留意相關的考量重點：  
  
-   網域使用者對裝載其所存取之主要匯入資料庫的遠端電腦必須擁有存取權限。  
  
-   指派為本機使用者角色的使用者無法使用分散式導覽。  
  
## <a name="administrator-accounts"></a>系統管理員帳戶  
 系統管理員必須是 securityadmin 或 sysadmin 群組的成員，才能授與權限給網域使用者。  
  
 若要執行 BAM 管理公用程式，您至少必須是 BAM 資料庫的資料庫操作員。  
  
## <a name="see-also"></a>另請參閱  
 [BAM 入口網站](../core/bam-portal.md)