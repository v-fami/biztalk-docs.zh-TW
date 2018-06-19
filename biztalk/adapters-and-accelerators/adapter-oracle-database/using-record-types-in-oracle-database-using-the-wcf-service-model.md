---
title: 使用 WCF 服務模型的 Oracle 資料庫中執行的作業使用的記錄類型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RECORD types, performing operations
- WCF service model, performing operations using RECORD types
ms.assetid: e7118a86-7470-48bb-aca0-6200dc0bb67c
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3de78290e29c4c1ddc1465e8a9463a6e9d7b86f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216254"
---
# <a name="run-operations-using-record-types-in-oracle-database-using-the-wcf-service-model"></a><span data-ttu-id="4632c-102">使用 WCF 服務模型的 Oracle 資料庫中執行的作業使用的記錄類型</span><span class="sxs-lookup"><span data-stu-id="4632c-102">Run Operations Using RECORD Types in Oracle Database using the WCF Service Model</span></span>
<span data-ttu-id="4632c-103">Oracle 記錄類型可用來代表階層式參數傳遞至 PL/SQL 函數和程序中的資訊。</span><span class="sxs-lookup"><span data-stu-id="4632c-103">Oracle RECORD types are used to represent hierarchical information in parameters passed to PL/SQL functions and procedures.</span></span> <span data-ttu-id="4632c-104">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現記錄類型為複雜的 XML 型別。</span><span class="sxs-lookup"><span data-stu-id="4632c-104">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces RECORD types as complex XML types.</span></span> <span data-ttu-id="4632c-105">在 WCF 服務模型中，會還原序列化強型別.NET 類別的記錄類型。</span><span class="sxs-lookup"><span data-stu-id="4632c-105">In the WCF service model, RECORD types are deserialized to strongly-typed .NET classes.</span></span> <span data-ttu-id="4632c-106">記錄欄位會表示為類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="4632c-106">The record fields are represented as properties on the class.</span></span>  
  
 <span data-ttu-id="4632c-107">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援下列幾種記錄類型：</span><span class="sxs-lookup"><span data-stu-id="4632c-107">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports the following kinds of RECORD types:</span></span>  
  
-   <span data-ttu-id="4632c-108">記錄會宣告為預存程序和函式中的資料表 %資料列型別參數的類型。</span><span class="sxs-lookup"><span data-stu-id="4632c-108">RECORD types that are declared as TABLE%ROWTYPE parameters in stored procedures and functions.</span></span>  
  
-   <span data-ttu-id="4632c-109">例如，宣告類型的記錄中當做參數的 PL/SQL 封裝的記錄類型`TYPE rec_type1 IS RECORD(name varchar2(100), age number(3));`</span><span class="sxs-lookup"><span data-stu-id="4632c-109">RECORD types that are declared as TYPE of RECORD parameters in PL/SQL packages for example, `TYPE rec_type1 IS RECORD(name varchar2(100), age number(3));`</span></span>  
  
-   <span data-ttu-id="4632c-110">包含巢狀的記錄的記錄類型。</span><span class="sxs-lookup"><span data-stu-id="4632c-110">RECORD types that contain nested records.</span></span>  
  
-   <span data-ttu-id="4632c-111">記錄中出現的類型為，逾時或在 OUT 參數的程序或函式。</span><span class="sxs-lookup"><span data-stu-id="4632c-111">RECORD types that appear as IN, OUT, or IN OUT parameters to procedures or functions.</span></span>  
  
-   <span data-ttu-id="4632c-112">傳回值的函式的記錄類型。</span><span class="sxs-lookup"><span data-stu-id="4632c-112">RECORD types that are RETURN values of functions.</span></span>  
  
 <span data-ttu-id="4632c-113">本主題說明如何在 WCF 服務模型中表示記錄類型。</span><span class="sxs-lookup"><span data-stu-id="4632c-113">This topic shows how RECORD types are represented in the WCF service model.</span></span> <span data-ttu-id="4632c-114">如需如何呼叫 Oracle 程序和函數的資訊，請參閱[叫用函式和 Oracle 資料庫使用 WCF 服務模型中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="4632c-114">For information about how to call Oracle procedures and functions, see [Invoke Functions and Procedures in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="4632c-115">關於本主題中使用的範例</span><span class="sxs-lookup"><span data-stu-id="4632c-115">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="4632c-116">本主題中的範例使用 SCOTT/ACCOUNT_PKG Oracle 的 PL/SQL 封裝。</span><span class="sxs-lookup"><span data-stu-id="4632c-116">The examples in this topic use the /SCOTT/ACCOUNT_PKG Oracle PL/SQL PACKAGE.</span></span> <span data-ttu-id="4632c-117">下列項目是從 ACCOUNT_PKG 來使用。</span><span class="sxs-lookup"><span data-stu-id="4632c-117">The following elements are used from ACCOUNT_PKG.</span></span>  
  
```  
TYPE address_rec_type IS RECORD (street customer.street%TYPE, city customer.city%TYPE, state customer.state%TYPE);  
  
FUNCTION create_account(acct IN ACCOUNT%ROWTYPE, addr IN address_rec_type) RETURN NUMBER;  
  
TYPE acctinfo_rec_type IS RECORD (acct account%ROWTYPE, address address_rec_type);  
  
FUNCTION get_accountinfo(aid NUMBER) RETURN acctinfo_rec_type;  
```  
  
 <span data-ttu-id="4632c-118">指令碼來產生此封裝隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="4632c-118">A script to generate this package is supplied with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] samples.</span></span> <span data-ttu-id="4632c-119">如需詳細資訊，請參閱指令碼</span><span class="sxs-lookup"><span data-stu-id="4632c-119">For more information, see the script</span></span>  
  
 <span data-ttu-id="4632c-120">如需這些範例的詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="4632c-120">For more information about the samples, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="record-types-in-the-wcf-service-model"></a><span data-ttu-id="4632c-121">WCF 服務模型中的記錄類型</span><span class="sxs-lookup"><span data-stu-id="4632c-121">RECORD Types in the WCF Service Model</span></span>  
 <span data-ttu-id="4632c-122">Oracle 記錄類型以複雜的 XML 型別，由[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4632c-122">Oracle RECORD types are represented as complex XML types by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="4632c-123">在 WCF 服務模型中，複雜的 XML 型別表示由類別，而此類別的屬性表示 Oracle 記錄類型的欄位。</span><span class="sxs-lookup"><span data-stu-id="4632c-123">In the WCF service model, complex XML types are represented by a class, and the properties of this class represent the fields of the Oracle RECORD type.</span></span> <span data-ttu-id="4632c-124">表示記錄型別參數的類別會封裝 （如果有的話） 和函式或程序的結構描述會限定命名空間中產生。</span><span class="sxs-lookup"><span data-stu-id="4632c-124">The class that represents a RECORD type parameter is generated in a namespace that is qualified by the PACKAGE (if any) and SCHEMA of the function or procedure.</span></span> <span data-ttu-id="4632c-125">此命名空間會唯一識別函式或程序的參數。</span><span class="sxs-lookup"><span data-stu-id="4632c-125">This namespace uniquely identifies the function or procedure of the parameter.</span></span> <span data-ttu-id="4632c-126">例如，下列命名空間中建立 Oracle 封裝 ACCOUNT_PKG CREATE_ACCOUNT 程序的記錄型別參數： `microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT`。</span><span class="sxs-lookup"><span data-stu-id="4632c-126">For example, the RECORD type parameters to the CREATE_ACCOUNT procedure in the Oracle PACKAGE ACCOUNT_PKG are created in the following namespace: `microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT`.</span></span> <span data-ttu-id="4632c-127">如需 WCF 服務模型中用來代表程序和函式中的複雜類型的命名空間的詳細資訊，請參閱[叫用函式和 Oracle 資料庫使用 WCF 服務模型中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="4632c-127">For more information about the namespaces used in the WCF service model to represent complex types in procedures and functions, see [Invoke Functions and Procedures in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
 <span data-ttu-id="4632c-128">記錄型別參數的命名空間由程序或函式，而產生的記錄型別參數的類別名稱是記錄類型宣告的方式決定。</span><span class="sxs-lookup"><span data-stu-id="4632c-128">While the namespace of a RECORD type parameter is determined by the procedure or function, the name of the class generated for the RECORD type parameter is determined by the way in which the RECORD type is declared.</span></span> <span data-ttu-id="4632c-129">下表顯示產生的類別名稱的方式根據宣告 Oracle 記錄型別參數的兩個不同的方式。</span><span class="sxs-lookup"><span data-stu-id="4632c-129">The following table shows how the name of the class is generated based on the two different ways of declaring the Oracle RECORD type parameter.</span></span>  
  
|<span data-ttu-id="4632c-130">Oracle 記錄類型</span><span class="sxs-lookup"><span data-stu-id="4632c-130">Oracle RECORD type</span></span>|<span data-ttu-id="4632c-131">名稱</span><span class="sxs-lookup"><span data-stu-id="4632c-131">Name</span></span>|<span data-ttu-id="4632c-132">範例</span><span class="sxs-lookup"><span data-stu-id="4632c-132">Example</span></span>|  
|------------------------|----------|-------------|  
|<span data-ttu-id="4632c-133">資料表 %rowtype 程序或函式參數</span><span class="sxs-lookup"><span data-stu-id="4632c-133">TABLE%ROWTYPE procedure or function parameter</span></span>|<span data-ttu-id="4632c-134">[PARAMETER_NAME]資料錄</span><span class="sxs-lookup"><span data-stu-id="4632c-134">[PARAMETER_NAME]RECORD</span></span>|<span data-ttu-id="4632c-135">ACCTRECORD</span><span class="sxs-lookup"><span data-stu-id="4632c-135">ACCTRECORD</span></span>|  
|<span data-ttu-id="4632c-136">記錄封裝參數的型別</span><span class="sxs-lookup"><span data-stu-id="4632c-136">TYPE of RECORD package parameter</span></span>|<span data-ttu-id="4632c-137">[PACKAGE_NAME][RECORD_TYPE_NAME]資料錄</span><span class="sxs-lookup"><span data-stu-id="4632c-137">[PACKAGE_NAME][RECORD_TYPE_NAME]RECORD</span></span>|<span data-ttu-id="4632c-138">ACCOUNT_PKGACCTINFO_REC_TYPERECORD</span><span class="sxs-lookup"><span data-stu-id="4632c-138">ACCOUNT_PKGACCTINFO_REC_TYPERECORD</span></span>|  
  
 <span data-ttu-id="4632c-139">[PARAMETER_NAME] = 程序或函式參數名稱。例如，帳戶</span><span class="sxs-lookup"><span data-stu-id="4632c-139">[PARAMETER_NAME] = the name of the procedure or function parameter; for example, ACCT.</span></span>  
  
 <span data-ttu-id="4632c-140">[PACKAGE_NAME] = Oracle 封裝的名稱。</span><span class="sxs-lookup"><span data-stu-id="4632c-140">[PACKAGE_NAME] = the name of the Oracle package.</span></span>  
  
 <span data-ttu-id="4632c-141">[RECORD_TYPE_NAME] = 記錄型別宣告; 中指定的名稱例如，ACCTINFO_REC_TYPE。</span><span class="sxs-lookup"><span data-stu-id="4632c-141">[RECORD_TYPE_NAME] = the name specified in the RECORD TYPE declaration; for example, ACCTINFO_REC_TYPE.</span></span>  
  
 <span data-ttu-id="4632c-142">下列程式碼會顯示為兩個 Oracle 函式產生 WCF 用戶端的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="4632c-142">The following code shows the method signatures of the WCF client generated for two Oracle functions.</span></span> <span data-ttu-id="4632c-143">/SCOTT/Package/ACCOUNT_PKG/CREATE_ACCOUNT 函式接受兩個簡單的記錄類型 IN 參數，而且 /SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTINFO 函數會傳回包含兩個巢狀的記錄類型的記錄型別參數。</span><span class="sxs-lookup"><span data-stu-id="4632c-143">The /SCOTT/Package/ACCOUNT_PKG/CREATE_ACCOUNT function takes two simple RECORD type IN parameters, and the /SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNTINFO function returns a RECORD type parameter that contains two nested RECORD types.</span></span> <span data-ttu-id="4632c-144">Oracle 函式宣告會包含在程式碼的頂端。</span><span class="sxs-lookup"><span data-stu-id="4632c-144">The Oracle function declarations are included at the top of the code.</span></span> <span data-ttu-id="4632c-145">每個函式的參數是唯一的命名空間所限定。</span><span class="sxs-lookup"><span data-stu-id="4632c-145">The parameters of each function are qualified by a unique namespace.</span></span>  
  
```  
FUNCTION create_account(acct IN ACCOUNT%ROWTYPE, addr IN address_rec_type) RETURN NUMBER;  
FUNCTION get_accountinfo(aid NUMBER) RETURN acctinfo_rec_type;  
  
public partial class SCOTTPackageACCOUNT_PKGClient : System.ServiceModel.ClientBase<SCOTTPackageACCOUNT_PKG>, SCOTTPackageACCOUNT_PKG {  
  
    ...  
  
    public System.Nullable<decimal> CREATE_ACCOUNT(microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT.ACCTRECORD ACCT, microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT.ACCOUNT_PKGADDRESS_REC_TYPERECORD ADDR);  
  
    public microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO.ACCOUNT_PKGACCTINFO_REC_TYPERECORD GET_ACCOUNTINFO(System.Nullable<decimal> AID);  
}  
```  
  
 <span data-ttu-id="4632c-146">下列程式碼顯示針對 CREATE_ACCOUNT 函式的參數產生的類別：`FUNCTION create_account(acct IN ACCOUNT%ROWTYPE, addr IN address_rec_type) RETURN NUMBER;`</span><span class="sxs-lookup"><span data-stu-id="4632c-146">The following code shows the classes generated for the parameters of the CREATE_ACCOUNT function: `FUNCTION create_account(acct IN ACCOUNT%ROWTYPE, addr IN address_rec_type) RETURN NUMBER;`</span></span>  
  
 <span data-ttu-id="4632c-147">此函式具有資料表 %rowtype 以宣告的參數和參數類型的記錄封裝類型宣告的參數 (`TYPE acctinfo_rec_type IS RECORD (acct account%ROWTYPE, address address_rec_type);`)。</span><span class="sxs-lookup"><span data-stu-id="4632c-147">This function has a parameter declared with a TABLE%ROWTYPE and a parameter declared with a TYPE of RECORD package type (`TYPE acctinfo_rec_type IS RECORD (acct account%ROWTYPE, address address_rec_type);`).</span></span>  
  
```  
namespace microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT {  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class ACCTRECORD : object, System.Runtime.Serialization.IExtensibleDataObject {…}  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class ACCOUNT_PKGADDRESS_REC_TYPERECORD : object, System.Runtime.Serialization.IExtensibleDataObject {…}  
  
}  
```  
  
### <a name="representation-of-a-simple-record-type"></a><span data-ttu-id="4632c-148">簡單記錄類型表示法</span><span class="sxs-lookup"><span data-stu-id="4632c-148">Representation of a Simple Record Type</span></span>  
 <span data-ttu-id="4632c-149">下列程式碼顯示簡單的記錄類型 WCF 服務模型中的呈現方式。</span><span class="sxs-lookup"><span data-stu-id="4632c-149">The following code shows how a simple RECORD type is represented in the WCF service model.</span></span> <span data-ttu-id="4632c-150">此程式碼會示範在展開之檢視的**ACCOUNTRECORD**代表 CREATE_ACCOUNT 函式中的帳戶 %資料列型別參數的類別。</span><span class="sxs-lookup"><span data-stu-id="4632c-150">This code shows the expanded view of the **ACCOUNTRECORD** class that represents the ACCOUNT%ROWTYPE parameter in the CREATE_ACCOUNT function.</span></span> <span data-ttu-id="4632c-151">這個類別，在記錄欄位 （資料列資料行） 會表示為屬性。</span><span class="sxs-lookup"><span data-stu-id="4632c-151">In this class, the record fields (row columns) are represented as properties.</span></span>  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
[System.Runtime.Serialization.DataContractAttribute()]  
public partial class ACCTRECORD : object, System.Runtime.Serialization.IExtensibleDataObject {  
  
    private System.Runtime.Serialization.ExtensionDataObject extensionDataField;  
  
    private System.Nullable<decimal> ACCTIDField;  
  
    private string NAMEField;  
  
    private System.Nullable<decimal> BALANCEField;  
  
    public System.Runtime.Serialization.ExtensionDataObject ExtensionData {  
        get {  
            return this.extensionDataField;  
        }  
        set {  
            this.extensionDataField = value;  
        }  
    }  
  
    [System.Runtime.Serialization.DataMemberAttribute()]  
    public System.Nullable<decimal> ACCTID {  
        get {  
            return this.ACCTIDField;  
        }  
        set {  
            this.ACCTIDField = value;  
        }  
    }  
  
    [System.Runtime.Serialization.DataMemberAttribute()]  
    public string NAME {  
        get {  
            return this.NAMEField;  
        }  
        set {  
            this.NAMEField = value;  
        }  
    }  
  
    [System.Runtime.Serialization.DataMemberAttribute(Order=2)]  
    public System.Nullable<decimal> BALANCE {  
        get {  
            return this.BALANCEField;  
        }  
        set {  
            this.BALANCEField = value;  
        }  
    }  
}  
```  
  
### <a name="representation-of-a-record-type-that-contains-nested-records"></a><span data-ttu-id="4632c-152">表示包含巢狀的記錄的記錄類型</span><span class="sxs-lookup"><span data-stu-id="4632c-152">Representation of a Record Type that Contains Nested Records</span></span>  
 <span data-ttu-id="4632c-153">下列程式碼顯示包含巢狀的記錄的記錄類型的表示法。</span><span class="sxs-lookup"><span data-stu-id="4632c-153">The following code shows the representation of a RECORD type that contains nested records.</span></span> <span data-ttu-id="4632c-154">此特定記錄類型為 GET_ACCOUNTINFO 函式的傳回值 (`FUNCTION get_accountinfo(aid NUMBER) RETURN acctinfo_rec_type;`)。</span><span class="sxs-lookup"><span data-stu-id="4632c-154">This particular RECORD type is the RETURN value of the GET_ACCOUNTINFO function (`FUNCTION get_accountinfo(aid NUMBER) RETURN acctinfo_rec_type;`).</span></span> <span data-ttu-id="4632c-155">ACCTINFO_REC_TYPE 為封裝參數使用的類型記錄建構宣告 (`TYPE acctinfo_rec_type IS RECORD (acct account%ROWTYPE, address address_rec_type);`)。</span><span class="sxs-lookup"><span data-stu-id="4632c-155">The ACCTINFO_REC_TYPE is a package parameter declared using a TYPE of RECORD construct (`TYPE acctinfo_rec_type IS RECORD (acct account%ROWTYPE, address address_rec_type);`).</span></span> <span data-ttu-id="4632c-156">它包含兩個巢狀簡單記錄類型、 資料表 %的資料列記錄和套件類型的記錄記錄。</span><span class="sxs-lookup"><span data-stu-id="4632c-156">It contains two nested simple record types, a TABLE%ROW record and a package TYPE of RECORD record.</span></span> <span data-ttu-id="4632c-157">這些兩個簡單的記錄在其父記錄相同的命名空間中宣告，並遵照預期的命名慣例。</span><span class="sxs-lookup"><span data-stu-id="4632c-157">These two simple records are declared in the same namespace as their parent record and follow the expected naming convention.</span></span>  
  
```  
namespace microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO {  
    using System.Runtime.Serialization;  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class ACCOUNT_PKGACCTINFO_REC_TYPERECORD : object, System.Runtime.Serialization.IExtensibleDataObject {  
  
        private System.Runtime.Serialization.ExtensionDataObject extensionDataField;  
  
        private microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO.ACCTRECORD ACCTField;  
  
        private microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO.ACCOUNT_PKGADDRESS_REC_TYPERECORD ADDRESSField;  
  
        public System.Runtime.Serialization.ExtensionDataObject ExtensionData {  
            get {  
                return this.extensionDataField;  
            }  
            set {  
                this.extensionDataField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute(IsRequired=true)]  
        public microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO.ACCTRECORD ACCT {  
            get {  
                return this.ACCTField;  
            }  
            set {  
                this.ACCTField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute(IsRequired=true)]  
        public microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO.ACCOUNT_PKGADDRESS_REC_TYPERECORD ADDRESS {  
            get {  
                return this.ADDRESSField;  
            }  
            set {  
                this.ADDRESSField = value;  
            }  
        }  
    }  
```  
  
## <a name="using-record-types-in-your-code"></a><span data-ttu-id="4632c-158">在您的程式碼中使用記錄類型</span><span class="sxs-lookup"><span data-stu-id="4632c-158">Using RECORD Types in Your Code</span></span>  
 <span data-ttu-id="4632c-159">在程式碼中使用記錄類型很簡單。</span><span class="sxs-lookup"><span data-stu-id="4632c-159">Using RECORD types in your code is straightforward.</span></span> <span data-ttu-id="4632c-160">要叫用程序或函式的記錄型別參數，您建立的記錄類型的執行個體，並將它傳遞至適當的方法中，WCF 用戶端上。</span><span class="sxs-lookup"><span data-stu-id="4632c-160">To invoke a procedure or function with a RECORD type parameter, you create an instance of the RECORD type or types and pass it to the appropriate method on the WCF client.</span></span> <span data-ttu-id="4632c-161">當程序或函式傳回時，您可以讀取屬性上任何 OUT 或 IN OUT 參數或函式傳回值會宣告為記錄類型。</span><span class="sxs-lookup"><span data-stu-id="4632c-161">When the procedure or function returns, you can read properties on any OUT or IN OUT parameters or function RETURN values that are declared as RECORD types.</span></span> <span data-ttu-id="4632c-162">如需如何使用 WCF 服務模型叫用程序和函數的詳細資訊，請參閱[叫用函式和 Oracle 資料庫使用 WCF 服務模型中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="4632c-162">For more information about how to invoke procedures and functions by using the WCF service model, see [Invoke Functions and Procedures in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4632c-163">Oracle 記錄型別參數 （和函式會傳回） 都會符合由其函式或程序 （和封裝） 的命名空間。</span><span class="sxs-lookup"><span data-stu-id="4632c-163">Oracle RECORD type parameters (and function returns) are qualified by the namespace of their function or procedure (and package).</span></span> <span data-ttu-id="4632c-164">這表示使用兩個不同的程序或函式中的記錄型別將會有不同的命名空間的每個程序或函式。</span><span class="sxs-lookup"><span data-stu-id="4632c-164">This means that a RECORD type that is used in two different procedures or functions will have a different namespace for each procedure or function.</span></span> <span data-ttu-id="4632c-165">您必須確定當您使用特定的程序或函式時正確地限定記錄型別。</span><span class="sxs-lookup"><span data-stu-id="4632c-165">You must be sure to qualify the RECORD type correctly when you use it for a specific procedure or function.</span></span> <span data-ttu-id="4632c-166">比方說，用做為 IN 參數，兩個不同的函式的記錄類型 （記錄類型的宣告） 的封裝將兩次在 WCF 用戶端程式碼中宣告，每個宣告對應至每個函式所產生的唯一命名空間。</span><span class="sxs-lookup"><span data-stu-id="4632c-166">For example, a package RECORD type (RECORD of TYPE declaration) that is used as an IN parameter to two different functions will be declared twice in the WCF client code with each declaration corresponding to the unique namespace generated for each function.</span></span> <span data-ttu-id="4632c-167">您必須確定您傳遞給每個個別的函式在參數上使用正確的命名空間。</span><span class="sxs-lookup"><span data-stu-id="4632c-167">You must be sure to use the correct namespace on the parameter that you pass to each respective function.</span></span>  
  
 <span data-ttu-id="4632c-168">在下列範例中，CREATE_ACCOUNT 函式會呼叫具有兩個簡單記錄參數。</span><span class="sxs-lookup"><span data-stu-id="4632c-168">In the following example, the CREATE_ACCOUNT function is called with two simple record parameters.</span></span> <span data-ttu-id="4632c-169">接下來，呼叫 GET_ACCOUNTINFO 函式。</span><span class="sxs-lookup"><span data-stu-id="4632c-169">Next, the GET_ACCOUNTINFO function is called.</span></span> <span data-ttu-id="4632c-170">此函數會傳回包含巢狀的記錄的記錄類型。</span><span class="sxs-lookup"><span data-stu-id="4632c-170">This function returns a RECORD type that contains nested records.</span></span> <span data-ttu-id="4632c-171">選取的欄位值從傳回的記錄寫入至主控台。</span><span class="sxs-lookup"><span data-stu-id="4632c-171">Selected field values from the returned RECORD are written to the console.</span></span> <span data-ttu-id="4632c-172">此範例中會省略步驟來設定 Oracle 資料庫的認證，以及開啟 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="4632c-172">Steps to set credentials for the Oracle database and to open the WCF client are omitted from this example.</span></span>  
  
```  
// Add WCF, WCF Adapter LOB SDK, and Oracle Database adapter namepaces  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
// Include this namespace for WCF Adapter LOB SDK and Oracle Database adapter exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
…  
  
// Create the client from configuration  
using (SCOTTPackageACCOUNT_PKGClient accountPkgClient = new SCOTTPackageACCOUNT_PKGClient("OracleDBBinding_SCOTT.Package.ACCOUNT_PKG"))  
{  
  
    ...  
  
    decimal acctId;  
  
    // Create an account record  
    // Note: ACCTRECORD is defined in both namespaces so specify the definition  
    // that corresponds to the client.  
  
    microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT.ACCTRECORD acctRec =   
        new microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT.ACCTRECORD();  
  
    // Set any value for ACCTID -- new account ID is returned by CREATE_ACCOUNT  
    acctRec.ACCTID = 0;  
    acctRec.NAME = "Anton Kirilov";  
    acctRec.BALANCE = 9583;  
  
    // Create address record  
    microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT.ACCOUNT_PKGADDRESS_REC_TYPERECORD addrRec = new microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.CREATE_ACCOUNT.ACCOUNT_PKGADDRESS_REC_TYPERECORD();  
    addrRec.STREET = "234 Main St";  
    addrRec.CITY = "Boston";  
    addrRec.STATE = "MA";  
  
    // Create account  
    try  
    {  
        acctId = (decimal)accountPkgClient.CREATE_ACCOUNT(acctRec, addrRec);  
    }  
    catch (Exception ex)  
    {  
        // handle exception  
        ...  
    }  
  
    ...  
  
    // Account info record  
    microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO.ACCOUNT_PKGACCTINFO_REC_TYPERECORD acctInfo =  
    new microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACCOUNTINFO.ACCOUNT_PKGACCTINFO_REC_TYPERECORD();  
  
    // Get account info for the account just created  
    // acctInfo is returned as a nested record type  
    try  
    {  
     acctInfo = accountPkgClient.GET_ACCOUNTINFO(acctId);  
    }  
    catch (Exception ex)  
    {  
    // handle exception  
    ...  
    }  
  
    // Write the account info to the console  
    Console.WriteLine("The account info is:");  
    Console.WriteLine("Name:\t\t\t{0}", acctInfo.ACCT.NAME);  
    Console.WriteLine("Street:\t\t\t{0}", acctInfo.ADDRESS.STREET);  
    Console.WriteLine("City:\t\t\t{0}", acctInfo.ADDRESS.CITY);  
    Console.WriteLine("State:\t\t\t{0}", acctInfo.ADDRESS.STATE);  
    Console.WriteLine("Account Id:\t\t{0}", acctInfo.ACCT.ACCTID);  
    Console.WriteLine("Account Balance:\t{0:C}", acctInfo.ACCT.BALANCE);  
  
    Console.WriteLine("\nHit <RETURN> to finish");  
    Console.ReadLine();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4632c-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4632c-173">See Also</span></span>  
 [<span data-ttu-id="4632c-174">開發使用 WCF 服務模型的 Oracle 資料庫應用程式</span><span class="sxs-lookup"><span data-stu-id="4632c-174">Develop Oracle Database applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)