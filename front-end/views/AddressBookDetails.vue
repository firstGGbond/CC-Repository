<template>
    <div class="area app-container mt-20">
        <SectionTitle>通讯录详情</SectionTitle>
        <el-card class="box-card">
            <div class="page-container">
                <div class="right-section">
                    <el-descriptions class="margin-top" :column="1" border>
                        <el-descriptions-item>
                            <template slot="label">
                                <i class="el-icon-office-building"></i>
                                姓名
                            </template>
                            {{ addressBook.realname }}
                        </el-descriptions-item>
                      <el-descriptions-item>
                        <template slot="label">
                          <i class="el-icon-office-building"></i>
                          电话
                        </template>
                        {{ addressBook.phone }}
                      </el-descriptions-item>
                      <el-descriptions-item>
                        <template slot="label">
                          <i class="el-icon-office-building"></i>
                          邮箱
                        </template>
                        {{ addressBook.email }}
                      </el-descriptions-item>
                        <el-descriptions-item>
                            <template slot="label">
                                <i class="el-icon-office-building"></i>
                                创建时间
                            </template>
                            {{ addressBook.createTime }}
                        </el-descriptions-item>
                    </el-descriptions>
                </div>

            </div>
            <div class="content" v-html="addressBook.content"></div>
        </el-card>
    </div>
</template>

<script>
import { findAddressBookByIdAPI } from "@/api/addressBook";

export default {
    data() {
        return {
            addressBook: {},
        };
    },
    async created() {
        const { data: addressBook } = await findAddressBookByIdAPI(this.$route.query.id);
        this.addressBook = addressBook;
    },
    methods: {},
};
</script>

<style lang="scss" scoped>
.box-card {
    width: 800px;
    margin: 20px auto;
}

.page-container {
    display: flex;

    .left-section {
        min-height: 500px;
        padding: 14px;

        .details-img {
            width: 80%;
            height: 300px;
        }
    }

    .right-section {
        padding: 14px;
        flex: 1;
    }
}
</style>
